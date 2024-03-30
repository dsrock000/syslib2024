# Week 11 Wordpress

### Download and extract

- Change directory to var/html/www

- Download the latest version of Wordpress from their website using wget `sudo wget https://wordpress.org/latest.tar.gz`

- Extract the package using tar `sudo tar -xzvf latest.tar.gz`

### Create Database and a User

- Switch to root user `sudo su`

- Load MySQL as root `mysql' -u root`

- Create a user for the Wordpress database `create user 'wordpress'@'localhost' identified by 'XXXXXXXXX';`

- Create the Wordpress database `create database wordpress;`

- Give new user full privileges to the database `grant all privileges on wordpress.* to 'wordpress'@'localhost';`

- `show databases;` to see the database and then quit MySQL `\q`

### Configure Wordpress

- Change directory to Wordpress

- Copy the sample configuration and rename it `sudo cp wp-config-sample.php wp-config.php`

- Edit the config file using nano `sudo nano wp-config.php`

- Input database name, user, and password into the config file

- Add the following command to the bottom of the file to disable FTP uploads to the site `define('FS_METHOD','direct');`

### Change File ownership

- Give access to Wordpress to write files in the base Wordpress directory by typing `sudo chown -R www-data:www-data /var/www/html/wordpress`

### Run the install script

- Use the IP for your server and go to this URL and setup a username and password for WordPress http://34.125.169.53/wordpress/wp-admin/install.php

### Reflections on Wordpress

- Themes are fun to play with, but can be dangerous. I switched to the Mindscape theme and it suggested using Kubio, which broke my WordPress. 

- I created new pages, uploaded media, changed the home page, and changed the menu.

- WordPress uses a lot of the same lingo as Drupal, but it's different enough to get me in trouble and slow me down. 

