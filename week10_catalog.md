# Week 10 Cataloging Module

### Create WebPage for data input

- Change directory to var/html/www

- Create new cataloging directory `sudo mkdir cataloging`

- Create new index.html file `sudo nano index.html`

- Insert html code from assignment that includes author, title, publisher, and copyright form inputs

- Save, close, and test new form by going to http://34.16.136.240/cataloging/ on browser

### Create PHP file to insert data from form into my database

- Create new index.php file `sudo nano index.php`
  
- Insert php code from assignment

- Change IP info to match my web server 34.16.136.240

### Security for web form

- Create authentication file within Apache2 `sudo htpasswd -c /etc/apache2/.htpasswd libcat`

- Edit Apache config file `sudo nano /etc/apache2/apache2.conf`

- Change the word None to All on line 172

- Change to the catalog directory `cd /var/www/html/cataloging`

-  Create a file to require username and password `sudo nano .htaccess`

-  Insert content from assignment and save file

-  Restart Apache2 `sudo systemctl restart apache2`

  ### Permissions and Ownership

- Directories where Apache needs to write data should be owned by www-data

- Change ownership of /var/www/html to www-data ` sudo chown :www-data /var/www/html`

- Change default for new files to be owned by www-data as well ` sudo chmod -R g+s /var/www/html`

  

  




