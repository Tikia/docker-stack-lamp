# docker-stack-lamp
## docker-php56-apache

Based on php:5.6-apache

Install :
- NTP, NTPdate
- curl, g++, zlib1g, libicu-dev, libmemcached-dev, libpq-dev, libjpeg-dev, libpng-dev, libfreetype6-dev, libssl-dev, libmcrypt-dev, libxml2-dev, libc-client-dev, libkrb5-dev, libldb-dev, libldap2-dev, librecode-dev, libtidy-dev
- php extensions : mcrypt, mysqli, pdo_mysql, mysql, pdo_pgsql, pgsql, gd, exif, ftp, imap, ldap, intl, simplexml, xml, tidy, xmlrpc, opcache, json, mbstring, recode, gettext, shmop, zip, dom, iconv, session, sockets
- letsencrypt.sh-apache2

Config Apache :
- Active module : rewrite ssl include status

Port exposed : 80

Volumes :
- httpdocs : /var/www/
- vHost conf : /etc/apache2/sites-enabled/
## docker-php7-apache

Based on php:7.2-apache

Install :
- NTP, NTPdate
- curl, g++, zlib1g, libicu-dev, libmemcached-dev, libpq-dev, libjpeg-dev, libpng-dev, libfreetype6-dev, libssl-dev, libmcrypt-dev, libxml2-dev, libc-client-dev, libkrb5-dev, libldb-dev, libldap2-dev, librecode-dev, libtidy-dev
- php extensions : mysqli, pdo_mysql, pdo_pgsql, pgsql, gd, exif, ftp, imap, ldap, intl, simplexml, xml, tidy, xmlrpc, opcache, json, mbstring, recode, gettext, shmop, zip, dom, iconv, session, sockets
- letsencrypt.sh-apache2

Config Apache :
- Active module : rewrite ssl include status

Port exposed : 80

Volumes :
- httpdocs : /var/www/
- vHost conf : /etc/apache2/sites-enabled/
## docker-mysql-server

From mysql/mysql-server

New MySQL 8.0.11 is using caching_sha2_password as default authentication method.

PhpMyAdmin cannot understand this authentication method.

So I create user with one of the older authentication method : CREATE USER xyz@localhost IDENTIFIED WITH mysql_native_password BY 'passw0rd'.

Another idea: as long as the phpmyadmin and other php tools don't work with it, just add this line to your file /etc/mysql/my.cnf : default_authentication_plugin = mysql_native_password

SRC : https://stackoverflow.com/questions/49948350/phpmyadmin-on-mysql-8-0
## docker-phpMyAdmin

From phpmyadmin/phpmyadmin:latest

--------------------------
MySQL 8 changed the default charset to utfmb4. But some clients don't know this charset. Hence when the server reports its default charset to the client, and the client doesn't know what the server means, it throws this error.

SRC : https://stackoverflow.com/questions/43437490/pdo-construct-server-sent-charset-255-unknown-to-the-client-please-rep
    

