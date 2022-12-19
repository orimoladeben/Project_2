## My Documentattion for Project 1

`sudo apt update`
`sudo apt install apache2`
`sudo systemctl status apache2`
![Apache Status](.\images\apache_status.PNG)
`curl http://localhost:80`
`http://<Public-IP-Address>:80`
![Public IP address check](./images/Public_IP_address_apache_works.PNG)
`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`
![Public IP address check in terminal](./images/Public_IP_address_apache_works_cp.PNG)


`sudo apt install mysql-server`
`sudo mysql`
![mysql successfully installed](./images/mysql_install_success.PNG)

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`
`mysql> exit`
`sudo mysql_secure_installation`
`sudo mysql -p`
`mysql> exit`
![mysql password validated](./images/validate_sql_password.PNG)

`sudo apt install php libapache2-mod-php php-mysql`
`php -v`
![php installed](./images/php_installed.PNG)

`sudo mkdir /var/www/projectlamp`
`sudo chown -R $USER:$USER /var/www/projectlamp`
`sudo vi /etc/apache2/sites-available/projectlamp.conf`
`sudo ls /etc/apache2/sites-available`
`sudo a2ensite projectlamp`
`sudo a2dissite 000-default`
`sudo apache2ctl configtest`
![projectlamp created with no syntax](./images/projectlamp_success_syntax.PNG)
`sudo systemctl reload apache2`
`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`
![website check codes in terminal](./images/website_check.PNG)
![website check page using public IP](./images/website_check_page.PNG)

`sudo vim /etc/apache2/mods-enabled/dir.conf`

`<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>`

`sudo systemctl reload apache2`
`vim /var/www/projectlamp/index.php`

`<?php
phpinfo();`
![PHP enabled info page](./images/php_enabled.PNG)
