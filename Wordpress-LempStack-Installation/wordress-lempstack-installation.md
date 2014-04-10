# Wordpress Installation on LEMP Server - Nginx, PHP-FPM, MySql

Note: This installation assumes you using Ubuntu 12.04 LTS Server or Ubuntu 12.04 LTS Desktop.

## Step 1: Update

```
sudo apt-get update
```

## Step 2: MySQL Installation and Setup

```
sudo apt-get install mysql-server
```

* Setup Wordpress database in MySql

```
mysql -u root -p
```

```
CREATE DATABASE wordpress;
```

```
CREATE USER wordpressuser@localhost;
```

```
SET PASSWORD FOR wordpressuser@localhost= PASSWORD("password");
```

```
GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost IDENTIFIED BY 'password';
```

```
FLUSH PRIVILEGES;
```

```
exit
```

## Step 3: Nginx Installation and Setup

```
sudo apt-get install nginx
```

* Setup nginx server block for wordpress

```
sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/wordpress
```

```
sudo nano /etc/nginx/sites-available/wordpress
```

> Add the following:

**Note:**rename example with your application name

```
server {
        server_name example.com www.example.com;

        access_log   /var/log/nginx/example.com.access.log;
        error_log    /var/log/nginx/example.com.error.log;

        root /home/user/path/sites/wordpress;
        index index.php;

        location / {
                try_files $uri $uri/ /index.php?$args;
        }

        location ~ \.php$ {
                try_files $uri =404;
                include fastcgi_params;
                #fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_pass 127.0.0.1:9000;
        }
}
```

>save and exit

* Activate the server block

```
sudo ln -s /etc/nginx/sites-available/wordpress /etc/nginx/sites-enabled/wordpress
```

```
sudo rm /etc/nginx/sites-enabled/default
```

> Restart Nginx

```
sudo service nginx restart
```

## Step 4: PHP Installation


```
sudo apt-get install php5-fpm
```

## Step 5: Download Wordpress

```
cd sites/
```

```
wget http://wordpress.org/latest.tar.gz
```

```
tar xvf latest.tar.gz
```

* Configure Wordpress

```
cd wordpress
```

```
cp wp-config-sample.php wp-config.php
```

```
sudo nano wp-config.php
```

**NOTE:** Enter the DBName, DBUser, and DBPassword that you created for wordpress database in mysql

```
// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'wordpress');
 
/** MySQL database username */
define('DB_USER', 'username');
 
/** MySQL database password */
define('DB_PASSWORD', 'password');
```

> save and exit

* Set the correct ownership to the directory

```
chown -R user:usergroup . 
```

```
usermod -a -G usergroup <user>
```

## Step 6: Install php5-mysql

```
sudo apt-get install php5-mysql
```

## Step 7: Restart Services

```
sudo service nginx restart
```

```
sudo service php5-fpm restart
```

## Step 8: add example.com to /etc/hosts

```
sudo nano /etc/hosts
```

```
127.0.0.1       example.com
```

## Step 9: Setup wp-admin panel

> Open your Browser and goto following address to setup your admin account

```
example.com/wp-admin/install.php
```

> To login into your wordpress dashboard

```
example.com/wp-admin
```

> And you are good to go..
