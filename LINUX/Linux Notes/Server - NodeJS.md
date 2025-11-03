--- Install ---
cd /opt/
sudo chmod -R 755 ./
tar xf node-v16.18.0-linux-x64.tar.xz

___

**Manjaro Linux:**
nano /home/andrew/.zshrc
Add the following lines to the end of file:

***NodeJS (export):***
export NODEJS_HOME=/mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin
export PATH=$NODEJS_HOME:$PATH

___

**Ubuntu:**
nano ~/.profile OR ~/.bashrc
Add the following lines to the end of file:

***NodeJS (export):***
export NODEJS_HOME=/mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin
export PATH=$NODEJS_HOME:$PATH

Alternative:
export PATH=$PATH:/mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin

___

node -v
npm -v
npm version

___

SymLinks (1):
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/node /usr/bin/node
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/npm /usr/bin/npm
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/npx /usr/bin/npx

Install:
sudo npm install -g npm@latest
sudo npm install -g firebase-tools@latest
sudo npm install -g sass@latest
sudo npm install -g less@latest
sudo npm install -g uglify-js@latest
sudo npm install -g yarn

SymLinks (2):
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/firebase /usr/bin/firebase
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/sass /usr/bin/sass
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/lessc /usr/bin/lessc
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/uglifyjs /usr/bin/uglifyjs

___

Optional:
sudo npm install -g yarn
sudo npm install -g gulp

Optional (SymLinks):
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/yarn /usr/bin/yarn
sudo ln -s /mnt/HDD_1/01_Apps/Apps_Portable/002/node/bin/gulp /usr/bin/gulp

####### sudo npm install -g gatsby-cli
####### sudo npm install -g @angular/cli

--- Delete Packages ---
sudo npm remove -g firebase-tools
sudo npm remove -g sass
sudo npm remove -g less
sudo npm remove -g uglify-js

--- Delete SymLinks ---
sudo rm /usr/bin/node
sudo rm /usr/bin/npm
sudo rm /usr/bin/npx
sudo rm /usr/bin/firebase
sudo rm /usr/bin/sass
sudo rm /usr/bin/lessc
sudo rm /usr/bin/uglifyjs