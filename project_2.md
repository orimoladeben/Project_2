`sudo apt update`

`sudo apt install nginx`

`sudo systemctl status nginx`

![nginx successfully installed](./images/nginx_install_1.PNG)

![nginx successfully installed and updated](./images/nginx_success_2.PNG)

`curl http://localhost:80`

`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`

![IP port confirmation](./images/nginx_IP_port_confirmation_3.PNG)

![nginx web confirmation](./images/nginx_success_finalwebpage_4.PNG)


`sudo apt install mysql-server`

`sudo mysql`

![mysql successfully installed](./images/mysql_success.PNG)

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

`mysql> exit`

`sudo mysql_secure_installation`

![mysql password validation page](./images/mysql_password_validation.PNG)

`sudo mysql -p`

![mysql final password test](./images/mysql_final_password_test.PNG)

`mysql> exit`

`sudo apt install php-fpm php-mysql`

![php successfully installed](./images/php_success_step3.PNG)

`sudo mkdir /var/www/projectLEMP`

`sudo chown -R $USER:$USER /var/www/projectLEMP`

`sudo nano /etc/nginx/sites-available/projectLEMP`

![nginx configuration nano](./images/Step4_configuring_nano1.PNG)

`sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`

`sudo nginx -t`

![nginx no syntax](./images/Step4_nginx_no_syntax.PNG)

`sudo unlink /etc/nginx/sites-enabled/default`

`sudo systemctl reload nginx`

`http://<Public-IP-Address>:80`

![nginx working webpage](./images/Step4_nginx_working_.PNG)

![nginx working terminal pic](./images/Step4_nginx_working_terminalpic.PNG)


`sudo nano /var/www/projectLEMP/info.php`

`<?php
phpinfo();`

`http://`server_domain_or_IP`/info.php`

![php info page](./images/Step5_php_info.PNG)

`sudo rm /var/www/your_domain/info.php`

`sudo mysql`

`mysql> CREATE DATABASE `example_database`;`

`mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';`

`mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';`

`mysql> exit`

`mysql -u example_user -p`

`mysql> SHOW DATABASES;`

![example_user databases](./images/Step6_example_user_example_database.PNG)

`CREATE TABLE example_database.todo_list (item_id INT AUTO_INCREMENT, content VARCHAR(255), PRIMARY KEY(item_id));`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("My second important item");`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("My third important item");`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("and this one more thing");`

`mysql>  SELECT * FROM example_database.todo_list;`

![insert example](./images/Step6_insert_example_database.PNG)

`mysql> exit`

`nano /var/www/projectLEMP/todo_list.php`

`<?php
$user = "example_user";
$password = "password";
$database = "example_database";
$table = "todo_list";

try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}`

`http://<Public_domain_or_IP>/todo_list.php`

![final php webpage mysql](./images/Step6_final_PHP_mysql.PNG)

