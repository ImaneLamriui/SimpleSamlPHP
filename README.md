# SimpleSamlPHP for secure access to web applications: Single Sign-On (SSO) and authorization.
## Prequisites: Apache2 Server + PHP 8.1.2 + mySQL V15.1 Distrib 10.6.12-MariaDB  Ubuntu Server 22.04 LTS 
###### sudo apt update & upgrade
### Add PPA repository for PHP 8.1:  
###### sudo add-apt-repository ppa:ondrej/php
###### vsudo apt update
###### sudo ap install apache2
###### sudo apt install php8.1 libapache2-mod-php8.1 php8.1-cli php8.1-mysql php8.1-json php8.1-opcache php8.1-mbstring php8.1-zip php8.1-fpm
###### sudo apt install mariadb-server
###### sudo a2enmod php8.1
###### sudo systemctl restart apache2
###### sudo nano /var/www/html/info.php
### Verify intallation: 
###### sudo nano /var/www/html/info.php
### Edit info.php:
###### info.php and add those lines:
<?php
phpinfo();
?>
###### verify on browser http://your-ip-direction/info.php
## SAML, which stands for "Security Assertion Markup Language," is a standard for exchanging authentication and authorization information between parties, particularly between a service provider and an identity provider. It is commonly used in web applications to facilitate Single Sign-On (SSO) and authorization.
### Download packages for SAML: sudo apt install php-xml php-mbstring php-curl php-memcache php-ldap memcached
## Database Configuration
### login Database
###### mysql -u root -p
### We will create a database that will serve as the authentication source. We will call it 'auth'
###### CREATE DATABASE auth DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
### We will create a separate MySQL user to work exclusively in our 'auth' database. From an administration and security standpoint, it is recommended to create databases and accounts in a functional manner:
###### GRANT ALL ON auth.* TO 'authuser'@'localhost' IDENTIFIED BY 'password';
### We will create a table named 'users' with two fields: 'username' and 'password'. For enhanced security, we will use the MySQL AES_ENCRYPT() function to encrypt the password string so that we do not store plain text passwords. This function encrypts a string and displays a binary string:
###### CREATE TABLE auth.users(username VARCHAR(30), password VARBINARY(30));
### We check if the database is created using the command 'SHOW DATABASES':
###### SHOW DATABASES;
### Create registers:
###### INSERT INTO auth.users(username, password) VALUES
###### ('user1', AES_ENCRYPT('user1pass','password')),
###### ('user2', AES_ENCRYPT('user2pass','password')),
### SimpleSAMLphp is an open-source implementation used to provide and to facilitate authentication and authorization services in web environments. Its primary purpose is to simplify and standardize the implementation of Single Sign-On (SSO) in web applications and services, especially in cases where secure and unified access to multiple applications and services is required. SAML is particularly useful in enterprise environments where multiple applications and services are present, aiming to simplify the login process for users. By implementing SAML, users can authenticate once and access multiple services without the need to log in repeatedly.
### There is a new stable release, versionV2.1.1, of SimpleSAMLphp with a different directory structure. The configuration files now come with an additional '.dist' extension, The '.dist' extension indicates that these are distribution files or templates intended for customization. Users should copy these files without the '.dist' extension and modify them according to their specific configuration.
### The 'www' directory has been replaced with 'public'."
### We establish a secret 'salt'. The simplesamlphp/config/config.php file will contain the password that we can edit, and additionally, a salt must be generated. It's important using a randomly generated and unique "salt" to enhance security in hash generation. It also emphasizes the crucial role of this process in SimpleSAMLphp configuration, warning against potential errors and underscoring the significance of improving overall system security. Attached image showing how to configure it.
###### openssl rand -base64 32
### There are some important configurations to consider to enable authentication, including activating the SQLAuth module. You can add this module to the authsources.php configuration file by setting 'sqlauth' to true. Ensure that you add the module if it is not already present in the configuration.
<p>Download <a href="https://github.com/simplesamlphp/simplesamlphp/releases/download/v2.1.1/simplesamlphp-2.1.1-full.tar.gz"> SimpleSamlPHP version2.1.1</a> </p>
<p>This version has many modifications. To get information on how to configure it correctly, you can refer to the documentation : </p><a href="https://simplesamlphp.org/docs/stable/index.html"> To learn more about the configuration settings...</a> </p>

