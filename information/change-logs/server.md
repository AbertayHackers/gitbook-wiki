# Server

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

