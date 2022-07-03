---
title: 'Raspberry Pi WordPress LAMP server: JUST the commands you need to make it happen'
date: '2021-10-02T14:37:00-07:00'
summary: 'If you have a Raspberry Pi and would like to turn it into a web server to host your own WordPress website, here are all the commands to make that happen. There is no fluff, just copy the commands one-by-one and you’ll have your site up and running in no time!'
draft: false
tags:
    - LAMP
    - Pi
    - Server
    - Web
---
If you have a Raspberry Pi and would like to turn it into a web server to host your own WordPress website, here are all the commands to make that happen. There is no fluff, just copy the commands one-by-one and you’ll have your site up and running in no time!

INSTALLING ALL APPS
===================

```
sudo apt update && upgrade
sudo apt install apache2
sudo apt install mariadb-server
sudo mysql_secure_installation
sudo apt install php-fpm php-mysql
sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip
sudo systemctl restart apache2
```

MySQL CONFIGURATION
===================
```
sudo mysql
```


```
CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;

```

```
CREATE USER  'USERNAME'@'localhost' IDENTIFIED BY 'PASSWORD';
```

```
GRANT ALL ON wordpress.* TO 'USERNAME'@'localhost' IDENTIFIED BY 'PASSWORD' WITH GRANT OPTION;
```

```
FLUSH PRIVILEGES;
```

```
mariadb -u USERNAME -p
```

```
SHOW DATABASES;
```

ALLOW PERMISSIONS TO THE MAIN WEBSITE DIRECTORY
===============================================

```
sudo mkdir /var/www/[yourdomain.com]
```

```
sudo chown -R $USER:$USER /var/www/[yourdomain.com]
```

```
sudo chown -R www-data:www-data /var/www/[yourdomain.com]
```

```
sudo find /var/www/[yourdomain.com] -type d -exec chmod 750 {} ;
```

```
sudo find /var/www/[yourdomain.com] -type f -exec chmod 640 {} ;
```

SERVER CONFIGURATION
====================

```
sudo nano /etc/apache2/sites-available/[yourdomain.com].conf
```

```
/var/www/[yourdomain.com]
AllowOverride All

<VirtualHost *:80>
ServerName yourdomain.com
ServerAlias www.yourdomain.com
ServerAdmin USERNAME@localhost
DocumentRoot /var/www/[yourdomain.com]
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

```
*Ctrl-X, Y, Enter*
```

```
sudo nano /var/www/[yourdomain].com/.htaccess
```

```
# BEGIN WordPress 
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>
# END WordPress
```

```
*Ctrl-X, Y, Enter*
```


## ENABLE SITE ON SERVER

```
sudo a2enmod rewrite
```

```
sudo a2ensite yourdomain.com
```

```
sudo a2dissite 000-default
```

```
sudo systemctl reload apache2
```

## INSTALL WORDPRESS

```
cd /var/www
```

```
sudo wget <a href="https://wordpress.org/latest.tar.gz">https://wordpress.org/latest.tar.gz</a>
```

```
sudo tar -xzvf latest.tar.gz
```

```
sudo rm latest.tar.gz
```

```
sudo mv wordpress yourdomain.com
```

## RELOAD APACHE TO ENSURE ALL SERVICES ARE STARTED

```
sudo systemctl reload apache2
```

#### REMINDER

*Verify port 80 AND 443 are forwarded on the router to your device*

*Remember to change your WordPress General settings to use https:// instead of http://*
 
___________

#### INSTALL LETSENCRYPT FOR SSL/HTTPS

```
sudo apt install snapd
```
```
sudo reboot
```
```
sudo snap install core; sudo snap refresh core
```
```
sudo apt-get remove certbot
```
```
sudo snap install --classic certbot
```
```
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
```
sudo certbot --apache
```

##### These last two commands are optional if you want to test the cert but will not affect functionality
```
sudo certbot certonly --apache

sudo certbot renew --dry-run
```

If you followed these instructions line-by-line, you should have a full website with SSL/HTTPS enabled and are ready to start blogging on WordPress!
Remember to install security plugins for your site and not to enable any other ports other than 80 and 443 through your home router.
Let me know if you make a website and link it in the comments! I'd love to see what you do!