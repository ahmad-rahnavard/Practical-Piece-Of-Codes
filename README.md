# Practical-Piece-Of-Codes

# Index

- [Docker](#docker-installation-arrow_up)
- [PHP](#php-installation-arrow_up)
- PHP Packages
	- [PHPUnit](#phpunit--arrow_up)
	- [PHP_CodeSniffer](#php_codesniffer-arrow_up)
	- [phpcpd](#phpcpd-arrow_up)
	- [PhpMetrics](#phpmetrics-arrow_up)
	- [PHPLOC](#phploc-arrow_up)
	- [PHPMD - PHP Mess Detector](#phpmd-php-mess-detector-arrow_up)
	- [dd for PHP](#dd-for-php-arrow_up)
- [Composer](#composer-installation-arrow_up)
	- [Composer permission problem](#composer-permission-problem-arrow_up) 
	- [Composer global installations problem](#composer-global-installations-problem-arrow_up) 
- Apache
	- [Change Default Port](#change-apache-default-port-to-a-custom-port-arrow_up)
	- [Create a virtual host](#create-a-virtual-host-arrow_up)
- [Nodjs](#nodjs-installation-arrow_up)
- [Laravel](#laravel-arrow_up)
	- [Laravel permissions](#laravel-permissions-arrow_up)
	- [Laravel link uploads folder](#laravel-link-uploads-folder-arrow_up)
	- [Laravel on shared host .htaccess](#laravel-on-shared-host-.htaccess-arrow_up)
- [Elasticsearch](#elasticsearch-arrow_up)
- [Linux](#linux-arrow_up)
	- [Load other drives automatically on start up](#load-other-drives-automatically-on-start-up-arrow_up)
	- [UFW](#ufw-arrow_up)
	- [Desktop icon](#desktop-icon-arrow_up)
	- [ISO to usb flash](#iso-to-usb-flash-arrow_up)
	- [Mime type](#mime-type-arrow_up)
	- [Activate pptp vpn on Debian Buster](#activate-pptp-vpn-on-debian-buster-arrow_up)
	- [Persian font problem](#persian-font-problem-arrow_up)
	- [Ubuntu dash to dock lock screen problem](#ubuntu-dash-to-dock-lock-screen-problem-arrow_up)
	- [Gimp error opening directory](#gimp-error-opening-directory-arrow_up)
	- [Colors in terminal](#colors-in-terminal-arrow_up)
	- [SWAP size](#swap-size-arrow_up)


# Docker installation [:arrow_up:](#index)
```bash
# Debian
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
# Ubuntu
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
```bash
# Verify that you now have the key with the fingerprin
sudo apt-key fingerprint 0EBFCD88
```
```bash
# Debian
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
# Ubuntu
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
```bash
sudo apt update
```
```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose
```
"Post install"
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
# newgrp docker
```
```bash
sudo mkdir /home/"$USER"/.docker
sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
sudo chmod g+rwx "$HOME/.docker" -R

# in some cases
sudo chmod 666 /var/run/docker.sock
```
```bash
sudo systemctl enable docker
```
# PHP installation [:arrow_up:](#index)
Debian 10 (Buster)
```bash
# default is php7.3
sudo apt-get install php
sudo apt-get install php-zip php-curl php-intl php-uuid php-amqp php-mongodb php-sqlite3 php-mysql php-gd php-soap php-pear php-dev php-mbstring php-xml php-cgi php-xml php-dom php-xdebug php-mysql sqlite php-sqlite3
```
```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get install php7.2
sudo apt-get install php7.2-zip php7.2-curl php7.2-intl php-uuid php-amqp php-mongodb php7.2-sqlite3 php7.2-mysql php7.2-gd php7.2-soap php-pear php7.2-dev php7.2-mbstring php7.2-xml php7.2-cgi php-xml php7.2-dom php7.2-xdebug php7.2-mysql sqlite php7.2-sqlite3
```
# [PHPUnit](https://phpunit.de/)  [:arrow_up:](#index)
```bash
composer global require phpunit/phpunit
```

# **[PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)** [:arrow_up:](#index)
```
composer global require "squizlabs/php_codesniffer=*"
```

# **[phpcpd](https://github.com/sebastianbergmann/phpcpd)** [:arrow_up:](#index)
Copy/Paste Detector (CPD) for PHP code.
```bash
composer global require sebastian/phpcpd
```
### Usage Example
```
$ phpcpd --fuzzy wordpress-4.9.8
phpcpd 4.1.0 by Sebastian Bergmann.

Found 66 clones with 3014 duplicated lines in 40 files:

  - /home/sb/wordpress-4.9.8/wp-includes/Requests/IRI.php:358-708 (350 lines)
    /home/sb/wordpress-4.9.8/wp-includes/SimplePie/IRI.php:404-754
.
.
.
  - /home/sb/wordpress-4.9.8/wp-includes/SimplePie/File.php:133-144 (11 lines)
    /home/sb/wordpress-4.9.8/wp-includes/SimplePie/File.php:215-226

0.86% duplicated lines out of 349460 total lines of code.
Average size of duplication is 45 lines, largest clone has 350 of lines

Time: 1.79 seconds, Memory: 272.00MB

```
# **[PhpMetrics](https://github.com/phpmetrics/PhpMetrics)** [:arrow_up:](#index)
PhpMetrics provides metrics about PHP project and classes, with beautiful and readable HTML report.
```bash
composer require phpmetrics/phpmetrics
```
```bash
php ./vendor/bin/phpmetrics --report-html=myreport .
```


# **[PHPLOC](https://github.com/sebastianbergmann/phploc)** [:arrow_up:](#index)
A tool for quickly measuring the size and analyzing the structure of a PHP project.
```bash
composer global require phploc/phploc
```
### Usage
```bash
phploc src
phploc 4.0.0 by Sebastian Bergmann.

Directories                                          3
Files                                               10

Size
  Lines of Code (LOC)                             1882
  Comment Lines of Code (CLOC)                     255 (13.55%)
  Non-Comment Lines of Code (NCLOC)               1627 (86.45%)
  .
  .
  .
```
# [PHPMD - PHP Mess Detector](https://phpmd.org/documentation/index.html) [:arrow_up:](#index)
It takes a given PHP source code base and look for several potential problems within that source. These problems can be things like:

-   Possible bugs
-   Suboptimal code
-   Overcomplicated expressions
-   Unused parameters, methods, properties
```bash
composer  global  require  phpmd/phpmd
```
### Usage
`phpmd [filename|directory] [report format] [ruleset file]`
`phpmd PHP/Depend/DbusUI/ xml rulesets/codesize.xml`
while
`rulesets/codesize.xml`:
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<pmd version="0.0.1" timestamp="2009-12-19T22:17:18+01:00">
  <file name="/projects/pdepend/PHP/Depend/DbusUI/ResultPrinter.php">
    <violation beginline="67"
               endline="224"
               rule="TooManyMethods"
               ruleset="Code Size Rules"
               package="PHP_Depend\DbusUI"
               class="PHP_Depend_DbusUI_ResultPrinter"
               priority="3">
      This class has too many methods, consider refactoring it.
    </violation>
  </file>
</pmd>
```
# dd for PHP [:arrow_up:](#index)
```php
<?php

function  dd($data) {
	highlight_string("<?php\n " . var_export($data, true) . "?>");
	echo '<script>document.getElementsByTagName("code")[0].getElementsByTagName("span")[1].remove();document.getElementsByTagName("code")[0].getElementsByTagName("span")[document.getElementsByTagName("code")[0].getElementsByTagName("span").length - 1].remove();</script>';
	die();
}

```
# Composer installation [:arrow_up:](#index)
[Composer website](https://getcomposer.org/download/)

```bash
#!/usr/bin/env bash
url='https://composer.github.io/pubkeys.html'
html=$( curl -# -L "${url}" 2> '/dev/null' )
hash=$(
<<< "${html}" \
grep -P -o -e '(?<=<pre>)(.*?)(?=<\/pre>)' |
head -n 1
)
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '${hash}') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
sudo php composer-setup.php --install-dir=/bin --filename=composer
php -r "unlink('composer-setup.php');"
```
```bash
#!/bin/sh

EXPECTED_SIGNATURE="$(wget -q -O - https://composer.github.io/installer.sig)"
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
ACTUAL_SIGNATURE="$(php -r "echo hash_file('sha384', 'composer-setup.php');")"

if [ "$EXPECTED_SIGNATURE" != "$ACTUAL_SIGNATURE" ]
then
    >&2 echo 'ERROR: Invalid installer signature'
    rm composer-setup.php
    exit 1
fi

php composer-setup.php --quiet --install-dir=/bin --filename=composer
RESULT=$?
rm composer-setup.php
exit $RESULT
```
### Composer permission problem [:arrow_up:](#index)
```bash
sudo chown $USER:$USER -R $HOME/.composer
#sudo chown $USER:$USER -R $HOME/.composer/cache/repo/https---packagist.org
#sudo chown $USER:$USER -R $HOME/.composer/cache/files/
```

### Composer global installations problem [:arrow_up:](#index)

```bash
sudo nano .bashrc
```
and add these in the end of the file
```bash
export PATH=$HOME/.config/composer/vendor/bin:$PATH
export PATH=$HOME/.composer/vendor/bin:$PATH
```

# Apache [:arrow_up:](#index)
### Change Apache Default Port To A Custom Port: [:arrow_up:](#index)
```bash
sudo nano /etc/apache2/ports.conf
```
```bash
# Listen 80
Listen 8090
```
```bash
sudo nano /etc/apache2/sites-enabled/000-default.conf
```
```bash
<VirtualHost *:8090>
```
```bash
sudo systemctl restart apache2
```
### Create a virtual host [:arrow_up:](#index)
```bash
sudo mkdir -p /var/www/html/example.dev/public_html
sudo nano /var/www/html/example.dev/public_html/index.html
# and put a test text
sudo chown -R $USER:$USER /var/www/html/example.dev/public_html
sudo chmod -R 755 /var/www/html/
```
```bash
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.dev.conf
```
```bash
sudo nano /etc/apache2/sites-available/example.dev.conf
```
```bash
<VirtualHost *:80>
 # The ServerName directive sets the request scheme, hostname and port that
 # the server uses to identify itself. This is used when creating
 # redirection URLs. In the context of virtual hosts, the ServerName
 # specifies what hostname must appear in the request's Host: header to
 # match this virtual host. For the default virtual host (this file) this
 # value is not decisive as it is used as a last resort host regardless.
 # However, you must set it for any further virtual host explicitly.
 #ServerName www.example.com

	ServerAdmin webmaster@example.dev
	ServerName example.dev
	ServerAlias www.example.dev
	DocumentRoot /var/www/html/example.dev/public_html

 # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
 # error, crit, alert, emerg.
 # It is also possible to configure the loglevel for particular
 # modules, e.g.
 # LogLevel info ssl:warn

 ErrorLog ${APACHE_LOG_DIR}/error.log
 CustomLog ${APACHE_LOG_DIR}/access.log combined

 # For most configuration files from conf-available/, which are
 # enabled or disabled at a global level, it is possible to
 # include a line for only one particular virtual host. For example the
 # following line enables the CGI configuration for this host only
 # after it has been globally disabled with "a2disconf".
 #Include conf-available/serve-cgi-bin.conf
</VirtualHost>
```
```bash
sudo a2dissite 000-default.conf
sudo a2ensite exmple.dev.conf
```
```bash
sudo systemctl restart apache2
```
```bash
sudo nano /etc/hosts
```
```bash
192.168.225.22 example.dev
```

# Nodjs installation [:arrow_up:](#index)
```bash
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs
```
#### Remove node_modules (cache error)
```bash
sudo rm -rf node_modules
```
???
```bash
sudo apt-get install libpng-dev
```
# Laravel [:arrow_up:](#index)

### Laravel permissions [:arrow_up:](#index)
```bash
sudo chown -R $USER:www-data storage
sudo chown -R $USER:www-data bootstrap/cache
sudo chmod -R 775 storage
sudo chmod -R 775 bootstrap/cache
```
### Laravel link uploads folder [:arrow_up:](#index)
```bash
ln -s ../storage/app/public/uploads uploads
```
### Laravel on shared host .htaccess [:arrow_up:](#index)
```
<IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteRule ^(.*)$ public/$1 [L]
</IfModule>
```

# Elasticsearch [:arrow_up:](#index)
```bash
sudo sysctl -w vm.max_map_count=262144
```
or
```bash
sudo nano /etc/sysctl.conf
```
and add

`vm.max_map_count=262144`

# Linux [:arrow_up:](#index)
## Load other drives automatically on start up [:arrow_up:](#index)
```bash
sudo nano /etc/fstab
```
then
```bash
UUID=*** /media/acer/A ntfs-3g defaults 0 0
```
or
```bash
/dev/sdb1 /media/acer/B ext4 defaults 0 0
```

## UFW [:arrow_up:](#index)
```bash
sudo apt install ufw
```
```bash
sudo nano /etc/default/ufw
```
:arrow_right: `IPV6=yes`
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```
Allow `ssh` `http` and `https`
```bash
sudo ufw allow 22
sudo ufw allow 80
sudo ufw allow 443
```
```bash
sudo ufw enable
```
UFW status
```bash
sudo ufw status numbered
```
Delete  a rule
```bash
sudo ufw delete 2
sudo ufw delete allow 80
```
Allow connection from an IP (to a port)
```bash
sudo ufw allow from 203.0.113.4
sudo ufw allow from 203.0.113.4 to any port 22
```
Deny connection from an IP
```bash
sudo ufw deny from 203.0.113.4
```
Esp
```bash
sudo ufw route allow proto tcp from any to any port 5601
sudo ufw route deny proto tcp from any to any port 5601
```
Disabling
```bash
sudo ufw disable
```
Reset
```bash
sudo ufw reset
```

## Desktop icon [:arrow_up:](#index)
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/opt/FileZilla/share/icons/hicolor/scalable/apps/filezilla.svg
Name[en_US]=FileZilla
Exec=/opt/FileZilla/bin/filezilla
Name=FileZilla
Icon=/opt/FileZilla/share/icons/hicolor/scalable/apps/filezilla.svg
```
## ISO to usb flash [:arrow_up:](#index)
Bootable USB:
```bash
dd if=./a.iso of=/dev/sdc bs=4M iflag=direct oflag=direct option=progress && sync
```
Formatting the USB
```bash
# wipe the drive
sudo wipefs --all /dev/sdc
# create partition
sudo cfdisk /dev/sdc
# -> select dos -> new -> enter (maximum size) -> primary -> write -> yes -> quit
# format the usb
sudo mkfs.ext4 -n 'USB Drive' /dev/sdc1
sudo mkfs.ntfs -n 'USB Drive' /dev/sdc1
sudo mkfs.vfat -n 'USB Drive' /dev/sdc1
```
## Mime type [:arrow_up:](#index)

```bash
sudo nano ~/.local/share/mime/packages/text-markdown.xml
```
With the following content:

```xml
<?xml version="1.0"?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
  <mime-type type="text/plain">
    <glob pattern="*.md"/>
    <glob pattern="*.mkd"/>
    <glob pattern="*.markdown"/>
  </mime-type>
</mime-info>

```

Then run:
```bash
update-mime-database ~/.local/share/mime
```
## Activate pptp vpn on Debian Buster [:arrow_up:](#index)
```bash
sudo apt install pptp-linux network-manager-pptp
```
not sure if needed from now on...
```bash
sudo apt install pptpd
```
```bash
sudo nano /etc/ppp/chap-secrets
```
and then add
```bash
usename<tab>vpnserver<tab>password
```

## Persian font problem [:arrow_up:](#index)
[Download farsi font](http://rastikerdar.github.io/)

Extract the downloaded fonts in `~/.fonts` directory
```bash
sudo nano ~/.fonts.conf
```
```xml
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
<match target="pattern">
<test name="family" qual="any">
<string>sans-serif</string>
</test>
<edit mode="assign" binding="same" name="family">
<string>Vazir</string>
</edit>
</match>
<dir>~/.fonts</dir>
</fontconfig>
```
## Ubuntu dash to dock lock screen problem [:arrow_up:](#index)
```bash
sudo mv /usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com ~/
```

## Gimp error opening directory [:arrow_up:](#index)
```bash
snap connect gimp:removable-media :removable-media
```
# Colors in terminal [:arrow_up:](#index)
```bash
BLACK=$(tput setaf 0)
RED=$(tput setaf 1)
GREEN=$(tput setaf 2)
YELLOW=$(tput setaf 3)
LIME_YELLOW=$(tput setaf 190)
POWDER_BLUE=$(tput setaf 153)
BLUE=$(tput setaf 4)
MAGENTA=$(tput setaf 5)
CYAN=$(tput setaf 6)
WHITE=$(tput setaf 7)
BRIGHT=$(tput bold)
NORMAL=$(tput sgr0)
BLINK=$(tput blink)
REVERSE=$(tput smso)
UNDERLINE=$(tput smul)

# e.g
echo "${RED}this is red ${NORMAL}this is normal"
```

# SWAP size [:arrow_up:](#index)

|RAM Size |Swap Size (Without Hibernation)  0|Swap size (With Hibernation) |
|---------|---------------------------------|-----------------------------|
|256MB	  |256MB	                    |512MB                        |
|512MB	  |512MB	                    |1GB                          |
|1GB	  |1GB	                            |2GB                          |
|2GB	  |1GB	                            |3GB                          |
|3GB	  |2GB	                            |5GB                          |
|4GB	  |2GB	                            |6GB                          |
|6GB	  |2GB	                            |8GB                          |
|8GB	  |3GB	                            |11GB                         |
|12GB	  |3GB	                            |15GB                         |
|16GB	  |4GB	                            |20GB                         |
|24GB	  |5GB	                            |29GB                         |
|32GB	  |6GB	                            |38GB                         |
|64GB	  |8GB	                            |72GB                         |
|128GB 	  |11GB	                            |139GB                        |
