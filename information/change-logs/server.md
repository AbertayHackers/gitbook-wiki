# Server

## 08/07/2021

* Moved all hacksoc/securi-tay sites from the old server to the new server
* Installed the Discord bot under a systemd service
* Created the discord.hacksoc.co.uk subdomain and set a holding page

## 17/06/2021

* Installed postfix and opendkim for a local SMTP server \(to be used for the Discord invite system\)
* Updated DNS accordingly to include SPF, DMARC and DKIM records
* Got the new VPS IP removed from a bunch of blocklists
  * Emails are now received by uni email accounts, so, mission accomplished
* Moved the bot across to the Hacksoc VPS

## 21/05/2021

* Started the new VPS replacing the old Debian 8 i386 droplet
* Installed:
  * Nginx \(Static files + Reverse Proxies\)
  * PHP
    * php-mysql
    * php-xml
    * php-zip
    * php-curl
    * php-gd
    * php-mbstring
    * php-imagick
  * Apache2 \(PHP Content, internal, to be proxied to\)
  * certbot
  * MariaDB
    * Secured MariaDB
* Created Nextcloud DB and DB User
* Added Nextcloud for internal filesharing
  * Sorted SSL cert
  * Uploaded Minutes so far
* Purged Snap for bloat

