# Week 13 Koha

*Instructions may not be 100% accurate. It took some tinkering to get everything working and I ran out of time to do instructions on the same day*

### Create New VM

- Go to Google Cloud Console
- Click on Compute Engine, VM instances
- Create instance
- Name VM
- Select E2 with 2 vCPU, 4 GB memory
- Change boot disk to Ubuntu
- Use Ubuntu 20.04 LTS x86/64
- Check allow HTTP traffic
- Leave other options as default and click Create

  ### Firewall Rule
- While still in Google Cloud console, click hamburger symbol at top left
- Click VPC Network, then Firewall
- Create a firewall rule, not a policy
- Name koha, port 8080
- Next to target, click on **All instances in the network**
- Source IPv4 ranges, add 0.0.0.0/0
- Click on TCP, add 8080 in the ports box
- Create

  ### Server Prep
- Update Server, clean up installers, install **gnupg2**, and reboot server
```
sudo apt update
sudo apt upgrade
sudo apt autoremove -y && sudo apt clean
sudo apt install gnupg2
sudo reboot now
```

### Koha Repository
- Add Koha repository to server and add digital signature
```
sudo su
echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list
wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -
```

### Install Koha
- Sync Repository and install Koha
```
apt update
apt install koha-common
```

### Configure Koha
- Edit Koha config file `nano /etc/koha/koha-sites.conf`
- Change **INTRAPORT="80"** to **INTRAPORT="8080"**
- Save and close the file
- Install MySQL `apt install mysql-server`
- Open MySQL `mysql -u root`
- Create MySQL username and password `create user 'kohauser'@'localhost' identified by 'XXXXXXXXX';` replacing XXXXs with password
- Create database `create database bibliolib;`
- Give privileges to our user `grant all privileges on bibliolib.* to 'kohauser'@'localhost';`
- Quit MySQL `\q`
- Enable URL rewriting `a2enmod rewrite`
- Enable CGI functionality `a2enmod cgi`
- Edit Apache ports file `nano /etc/apache2/ports.conf`
- Add `Listen 8080` to the bottom of this file, then save and close
- Test Apache config `apachectl configtest`
- Restart Apache `systemctl restart apache2`
- Disable Apache2 setup, enable traffic compression using deflate, enable bibliolib site, then reload apache
```
a2dissite 000-default
a2enmod deflate
a2ensite bibliolib
systemctl reload apache2
systemctl restart apache2
```

### Koha Web Installer
- Find Koha username and password in this file `nano /etc/koha/sites/bibliolib/koha-conf.xml`
- Go to the start of the config info on line number 252. Write down the username and password.
- Go to the URL of your server to begin the installer http://IP-ADDRESS:8080
- Use the [Koha Manual](https://koha-community.org/manual//22.11/en/html/installation.html) to assist with setup

### Reflections 
- Assignment was challenging and rewarding this week
- Koha is complicated and not easy to learn
- Koha Inventory was difficult to figure out on my own. I created records, but could never find them when searching.
- I could spend many more hours trying to learn and test in Koha. Since I have no Library background, a lot of the terminology goes over my head.
  










