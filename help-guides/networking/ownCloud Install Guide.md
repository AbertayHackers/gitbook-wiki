# ownCloud Install Guide

*An install guide by [Jack](https://wiki.hacksoc.co.uk/user/jack)*

ownCloud is an open-source, self-hosted, free file sharing platform. The biggest advantage of ownCloud over a service like Google Drive or Dropbox is that you are in control of your data.

For this installation ownCloud 9.1.1 is installed on Ubuntu 15.10. First, update the repositories and Linux distribution:

```sh
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Ensure you assign the server a static IP address on your network so that it never changes. The next step is to install tasksel (a custom installer used to install the LAMP stack). The LAMP stack is a platform that has services such as Apache and MySQL pre-installed.

```sh
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

This will open a GUI to set up MySQL with a user account and password. Follow the steps shown.

By default, ownCloud allows a maximum file upload size of 2 megabytes. This can be increased by editing the file php.ini found in /etc/php5/apache2/ and changing the *upload_max_filesize* variable.

The MySQL database now needs to be set up with user accounts. Enter the following command into the console:

```sh
MySQL -u root -p
```

This will prompt for the MySQL root user's password you previously configured. Enter this and you will get a MySQL shell. Enter the following commands to set up a table for users.

```sql
CREATE DATABASE <database name>;
CREATE USER '<username>'@'<localhost>' IDENTIFIED BY '<password>';
GRANT ALL PRIVILEGES ON <database name>.* TO ‘<username>’@’<localhost>’;
FLUSH PRIVILEGES;
exit
```

Download ownCloud from owncloud.org (Download available from https://owncloud.org/install/) and unzip the .zip file.

```sh
sudo unzip owncloud-9.1.1.zip
```

Move the ownCloud files to the WWW web directory so Apache can find them.

```sh
sudo mv owncloud /var/www
```

Make apache the owner of the directory so it has permissions to access and edit the files.

```sh
sudo chown -R www-data:www-data /var/www/owncloud
```

Edit the apache virtual host file (000-default.conf) found in /etc/apache2/sites-available/ to tell apache to point to the ownCloud directory. This means, for example, the default Apache landing page will be replaced with the ownCloud landing page.

Change the DocumentRoot within the configuration file to:

```sh
DocumentRoot /var/www/owncloud
```

Some additional PHP modules (that include a graphics library and a library for getting files from a HTTP server) that were not included with the LAMP stack are required for ownCloud to work must be installed.

```sh
sudo apt-get install php5-gd && sudo apt-get install php5-curl
```

Restart the Apache service to make the changes take effect.

```sh
sudo service Apache2 restart
```

From this point ownCloud is set up and running. Navigating to [http://127.0.0.1](http://127.0.0.1/) or the server's IP address in a browser will show the ownCloud homepage.

**Some Extra Considerations**

Although ownCloud is working, you may want to add some extra features to improve the user experience. One such recommendation is associating a domain name you own (instead of trying to remember the server IP address). The first step is to update the A record on your domain registrar’s website to match the public IP address of your home network. Next, edit the configuration file 000-default.conf found in /etc/apache2/sites-available/. Uncomment the *ServerName* variable and add your domain. You may also be required to set up port-forwarding, although setting this up will vary depending on the model of router you use.

```
ServerName www.example.com
```

Below the *DocumentRoot* variable, you will also want to add the following lines of code to fix some errors the ownCloud homepage displays:

```html
<Directory /var/www/owncloud>Options FollowSymLinks AllowOverride All
Order allow,deny
allow from all
</Directory>
```

Another consideration is adding HTTPS support. Without this, usernames, passwords and any files sent to the server are sent unencrypted. Guide for adding this will be available soon.

------

If you have any problems with the configuration of ownCloud, feedback or suggestions on the guide message me on the Slack channel @jack or on [Twitter](https://twitter.com/iJackWilson).