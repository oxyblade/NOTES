> ```
> systemctl status apache2.service | grep -inE 'Active:' && systemctl status mysql.service | grep -inE 'Active:'
> ```
> ```
> systemctl status apache2.service | grep -inE 'Active:' && systemctl status apache2-isp@php74.service | grep -inE 'Active:' && systemctl status mysql.service | grep -inE 'Active:'
> ```
> ```
> systemctl restart apache2.service
> ```
> ```
> systemctl restart apache2-isp@php74.service
> ```
> ```
> systemctl restart mysql.service
> ```
> ```
> systemctl restart apache2.service && systemctl restart apache2-isp@php74.service && systemctl restart mysql.service
> ```

> ```
> systemctl status apache2.service | grep -inE 'Active:' && systemctl status mariadb.service | grep -inE 'Active:'
> ```
> ```
> systemctl restart apache2.service
> ```
> ```
> systemctl restart mariadb.service
> ```
> ```
> systemctl restart apache2.service && systemctl restart mariadb.service
> ```
### *APACHE*
sudo apt-get update
sudo apt-get install apache2

sudo systemctl status apache2.service
sudo systemctl start apache2.service
sudo systemctl stop apache2.service
sudo systemctl reload apache2.service
sudo systemctl restart apache2.service
sudo systemctl enable apache2.service ( Launch at reboot )
sudo systemctl disable apache2.service

--- Manjaro Linux ---
sudo systemctl status httpd.service
sudo systemctl start httpd.service
sudo systemctl stop httpd.service
sudo systemctl reload httpd.service
sudo systemctl restart httpd.service
sudo systemctl enable httpd.service ( Launch at reboot )
sudo systemctl disable httpd.service

apachectl configtest - Check Apache Syntax

--- enable mod_rewrite for .htaccess ---
sudo a2enmod rewrite

--- apache2.conf --- (1)
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride All
	Require all granted
</Directory>

--- apache2.conf --- (2)
ServerName 127.0.0.1 - Add this line to the end of the file

--- /etc/hosts --- (3)
127.0.0.1	server0 (...and etc.)

- Security -
ServerTokens Productonly
ServerSignature off

Timeout 600

--- apache2.conf --- add after line AccessFileName .htaccess ---
LimitRequestLine 1000000
LimitRequestFieldSize 1000000

___

### nginx
***Block Bots***
/etc/nginx/vhosts-includes/bad_bot.conf
/etc/nginx/vhosts-includes/bad_bot.conf
/etc/nginx/vhosts-includes/badbot.conf
nano /etc/nginx/vhosts-includes/badbot.conf
systemctl restart nginx.service
systemctl status nginx.service
nginx -t (test the configuration file: nginx checks the configuration for correct syntax, and then tries to open files referred in the configuration)
nginx -T (same as `-t`, but additionally dump configuration files to standard output)
nginx -T | grep include

___
### *MySQL*
sudo apt-get update
sudo apt-get install mysql-server mysql-client
sudo mysql_secure_installation

sudo systemctl status mysql.service
sudo systemctl start mysql.service
sudo systemctl stop mysql.service
sudo systemctl restart mysql.service

sudo ufw allow mysql ( Allow remote access )
sudo systemctl enable mysql.service ( Launch at reboot )
sudo systemctl disable mysql.service

Create a MySQL Database:
sudo mysql -u root -p
CREATE DATABASE dbname;
GRANT ALL PRIVILEGES ON *dbname* TO 'login_db_here'@'localhost' IDENTIFIED BY 'password_db_here';
FLUSH PRIVILEGES;
quit;

show databases;
USE dbname;
You can now work with the database...

mysql> drop database name_db; ( Delete Database )

--- Troubleshooting ---

warning: current start runlevel(s) (empty) of script `mysql' overrides LSB defaults (2 3 4 5);
warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `mysql' overrides LSB defaults (0 1 6);
sudo update-rc.d mysql enable

___
### *PHP*
**Repositories**
sudo add-apt-repository ppa:ondrej/apache2
sudo add-apt-repository ppa:ondrej/php
sudo apt-get install php8.1
sudo apt-get install php8.1-fpm

sudo apt-get install php7.4 php7.4-{xml,mysql,zip,intl,imap,ldap,gd,cli,bz2,curl,mbstring,pgsql,opcache,soap,cgi,imagick,xdebug}
sudo apt-get install php8.0 php8.0-{xml,mysql,zip,intl,imap,ldap,gd,cli,bz2,curl,mbstring,pgsql,opcache,soap,cgi,imagick,xdebug}
sudo apt-get install php8.1 php8.1-{xml,mysql,zip,intl,imap,ldap,gd,cli,bz2,curl,mbstring,pgsql,opcache,soap,cgi,imagick,xdebug}

sudo apt-get install libapache2-mod-php
sudo apt-get install libapache2-mod-php7.4
sudo apt-get install libapache2-mod-php8.0
sudo apt-get install libapache2-mod-php8.1

**Configure PHP**
/etc/php/8.0/apache2/php.ini

memory_limit = 256M - 512M (1024M - 1280000000000000000000M) [memory_limit > post_max_size]
post_max_size = 128M - 256M (768M - 1024M - 4096456M) [post_max_size >= upload_max_filesize]
upload_max_filesize = 128M - 256M (512M - 750M - 1024M - 40964564M)
max_execution_time = 6000 (30 - 120 - 300 - 6000 - 3000000)
max_input_vars = 100000 (1000 - 5000 - 100000)
max_input_time = -1 (-1 - 60 - 1000 - 60000000000000)
####### max_file_uploads = 200

expose_php = Off            # Identify PHP Info

/opt/lampp/phpmyadmin/libraries/config.default.php
$cfg['ExecTimeLimit'] = 0;

/etc/php/7.4/fpm/php.ini (Отредактируем конфиг PHP-FPM)
cgi.fix_pathinfo=0 (Устанавливаем cgi.fix_pathinfo в 0)
(устранение уязвимости исполнения файлов)

**Switch PHP Version**
sudo a2dismod php8.1
sudo a2enmod php8.0
sudo systemctl restart apache2
sudo service apache2 restart

sudo update-alternatives --config php
sudo service apache2 restart

**phpX.X-fpm.service**
sudo systemctl enable php7.4-fpm.service ( Launch at reboot )
sudo systemctl disable php7.4-fpm.service

sudo systemctl status php7.4-fpm.service
sudo systemctl start php7.4-fpm.service
sudo systemctl stop php7.4-fpm.service
sudo systemctl reload php7.4-fpm.service
sudo systemctl restart php7.4-fpm.service

OR:

sudo service php7.4-fpm start
sudo service php7.4-fpm stop
sudo service php7.4-fpm restart
sudo service php7.4-fpm reload

----------------------------------------

sudo apt install php7.1-mcrypt
sudo systemctl restart apache2

----------------------------------------

php -i | grep mysql
sudo dpkg-reconfigure -plow phpmyadmin

___
### *PhpMyAdmin*
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin.conf
sudo systemctl restart apache2

--- root access (login & password) (/etc/mysql/debian.cnf) ---

/etc/phpmyadmin/config.inc.php
/* User for advanced features */
$cfg['Servers'][$i]['controluser'] = 'phpmyadmin'; 
$cfg['Servers'][$i]['controlpass'] = 'password_here';

___
### *MISC*

**WordPress**
/var/www/zdorovajastrana.com/public_html/wp-content/themes/zdorovajastrana
Here can be written next commands:
composer install
yarn install (make dependencies...)
yarn build (Compiling)

**yarn package manager**
yarn start — Compile assets when file changes are made, start Browersync session
yarn build — Compile and optimize the files in your assets directory
yarn build:production — Compile assets for production

sudo apt-get install libpng16-dev (When ERROR compile 'yarn build:production' )

npm install -g browser-sync (Synchronise browser testing)

Change PASSWORD or LOGIN wp-admin:
sudo mysql -u root –p
use db_name;
UPDATE wp_users SET user_pass = MD5('new_password') WHERE user_login = 'current_login_name';
UPDATE wp_users SET user_login='new_login_name' WHERE user_login='old_login_name';
quit;

___

**Composer (Dependency Manager for PHP)**
/var/www/testserver.com/public_html/wp-content/themes/

**Download Composer:**
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"

composer create-project roots/sage mythemename
/var/www/testserver.com/public_html/wp-content/themes/mythemename/
yarn
yarn start

yarn add gulp --dev
yarn add gulp-sass --dev