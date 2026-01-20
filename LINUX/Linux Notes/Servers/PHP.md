### Configure PHP
/etc/php/8.0/apache2/php.ini

memory_limit = 256M - 512M (1024M - 1280000000000000000000M) [memory_limit > post_max_size]
post_max_size = 128M - 256M (768M - 1024M - 4096456M) [post_max_size >= upload_max_filesize]
upload_max_filesize = 128M - 256M (512M - 750M - 1024M - 40964564M)
max_execution_time = 6000 (300 - 3000000)
max_input_vars = 100000 (5000 - 100000)
max_input_time = -1 (-1 - 1000 - 60000000000000)
####### max_file_uploads = 200

expose_php = Off            # Identify PHP Info

___

