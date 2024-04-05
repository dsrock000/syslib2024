# Week 12 Omeka

### Prerequisites

- Install Image Magick to for pictures and thumbnails in Omeka `sudo apt install imagemagick`

- Enable Apache module to help rewrite URLs `sudo a2enmod rewrite`

- Install unzip to extract Omeka installer `sudo apt install unzip`

- Restart Apache `sudo systemctl restart apache2`

### Create user and database

- Switch to root `sudo su`

- Open MySQL `mysql -u root`

- Create user and password for Omeka database `create user 'omekauser'@'localhost' identified by 'XXXXXXXXX';` and replace XXXXXX with your password

- Create Omeka database `create database omeka;`

- Give priviles to Omeka database to new user `grant all privileges on omeka.* to 'omekauser'@'localhost';`

- Check database `show databases;`

- Quit MySQL `\q`

### Download and Install Omeka

- Download Omeka `sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip`

- Extract installer `sudo unzip omeka-3.1.2.zip` while in /var/www/html

- Rename directory with extracted installer `sudo mv omeka-3.1.2 omeka`

- Configure Omeka `sudo nano db.ini` while in the omeka directory

- Change host to localhost and add new Omeka account to username and password.

- Change ownership to www-data for Omeka directory `sudo chown -R www-data:www-data /var/www/html/omeka/files`

- Visit http://34.125.169.53/omeka/ and complete setup of Omeka

### Reflections

- I haven't used Omeka before. I can see how it will work well in a library setting. 

- I see all the lessons coming together. Surely there is a way to import the data of the books from previous assignments, but so far it alludes me. 
