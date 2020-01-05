
## Index
- [Docker](#docker-menu-arrow_up)
- [Apache](#apache-menu-arrow_up)
- [Git](#git-menu-arrow_up)
- [PhpStorm](#phpstorm-menu-arrow_up)
- [VSCode](#vscode-menu-arrow_up)
- [VIM](#vim-menu-arrow_up)
- [Elasticsearch](#elasticsearch-menu-arrow_up)
- [Composer](#composer-menu-arrow_up)
- [Laravel](#laravel-menu-arrow_up)
- [MySQL](#mysql-menu-arrow_up)
- [PHP](#php-menu-arrow_up)
- [Nodjs](#nodjs-menu-arrow_up)
- [Postman](#postman-menu-arrow_up)
- [Linux](#linux-menu-arrow_up)
- [Windows](#windows-menu-arrow_up)

******************************************
##### Docker menu [:arrow_up:](#index)
* [Docker installation](#docker-installation-arrow_up)
* [Post install](#post-install-arrow_up)
* [Docker Compose](#docker-compose-arrow_up)
* [Copy From Container](#copy-from-container-arrow_up)
* [List Container IPs](#list-container-ips-arrow_up)
******************************************
##### Apache menu [:arrow_up:](#index)
* [Change Default Port](#change-apache-default-port-to-a-custom-port-arrow_up)
* [Create a virtual host](#create-a-virtual-host-arrow_up)
******************************************
##### Git menu [:arrow_up:](#index)
* [Git log](#git-log-arrow_up)
******************************************
##### PhpStorm menu [:arrow_up:](#index)
* [PhpStorm](#phpstorm-arrow_up)
******************************************
##### VSCode menu [:arrow_up:](#index)
* [VSCode](#vscode-arrow_up)
******************************************
##### VIM menu [:arrow_up:](#index)
* [VIM](#vim-arrow_up)
******************************************
##### Elasticsearch menu [:arrow_up:](#index)
* [Elasticsearch](#elasticsearch-arrow_up)
******************************************
##### Composer menu [:arrow_up:](#index)
* [Composer installation](#composer-installation-arrow_up)
* [Composer permission problem](#composer-permission-problem-arrow_up)
* [Composer global installations problem](#composer-global-installations-problem-arrow_up)
******************************************
##### Laravel menu [:arrow_up:](#index)
* [Laravel permissions](#laravel-permissions-arrow_up)
* [Laravel link uploads folder](#avel-link-uploads-folder-arrow_up)
* [Laravel on shared host .htaccess](#laravel-on-shared-host-.htaccess-arrow_up)
* [Laravel IDE helper](#laravel-ide-helper-arrow_up)
* [Laravel log regex](#laravel-log-regex-arrow_up)
******************************************
##### MySQL menu [:arrow_up:](#index)
* [MySql Export](#mysql-export-arrow_up)
******************************************
##### PHP menu [:arrow_up:](#index)
* [PHPUnit](#phpunit-arrow_up)
* [PHP_CodeSniffer](#php_codesniffer-arrow_up)
* [phpcpd](#phpcpd-arrow_up)
* [PhpMetrics](#phpmetrics-arrow_up)
* [PHPLOC](#phploc-arrow_up)
* [PHPMD - PHP Mess Detector](#phpmd---php-mess-detector-arrow_up)
* [dd for PHP](#dd-for-php-arrow_up)
* [PHP Elvis ?: and Null Coalescing ?? operators](#php-elvis--and-null-coalescing--operators-arrow_up)
* [User Agent device](#user-agent-device-arrow_up)
******************************************
##### Elasticsearch menu [:arrow_up:](#index)
* [Elasticsearch Max Map Count](#elasticsearch-vm-max-map-count-arrow_up)
******************************************
##### Nodjs menu [:arrow_up:](#index)
* [npm installation](#npm-installation-arrow_up)
* [npm permission problem](#npm-permission-problem-arrow_up)
******************************************
##### Postman menu [:arrow_up:](#index)
* [Postman Pre-Requests](#postman-pre-requests-arrow_up)
******************************************
##### Linux menu [:arrow_up:](#index)
* [Load other drives automatically on start up](#load-other-drives-automatically-on-start-up-arrow_up)
* [Wifi deriver](#wifi-deriver-arrow_up)
* [Bluetooth headsets problem (Output devices setting)](#bluetooth-headsets-problem-arrow_up)
* [UFW](#ufw-arrow_up)
* [Network restart Ubuntu](#network-restart-ubuntu-arrow_up)
* [Desktop icon](#desktop-icon-arrow_up)
* [ISO to usb flash](#iso-to-usb-flash-arrow_up)
* [Mime type](#mime-type-arrow_up)
* [Activate pptp vpn on Debian Buster](#activate-pptp-vpn-on-debian-buster-arrow_up)
* [Persian font problem](#persian-font-problem-arrow_up)
* [Ubuntu dash to dock lock screen problem](#ubuntu-dash-to-dock-lock-screen-problem-arrow_up)
* [Gimp error opening directory](#gimp-error-opening-directory-arrow_up)
* [Colors in terminal](#colors-in-terminal-arrow_up)
* [SWAP size](#swap-size-arrow_up)
* [Upgrade only one package](#upgrade-only-one-package-arrow_up)
* [Tmux](#tmux-arrow_up)
* [Copy Progress](#copy-progress-arrow_up)
* [VLC](#vlc-arrow_up)
* [Custom gestures](#custom-gestures-arrow_up)
* [Enpass browser sync problem](#enpass-browser-sync-problem-arrow_up)
******************************************
##### Windows menu [:arrow_up:](#index)
* [MBR to GPT](#mbr-to-gpt-arrow_up)
* [Windows Enterprise Activation](#windows-enterprise-activation-arrow_up)


# Docker [:arrow_up:](#index)
### Docker installation [:arrow_up:](#index)
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
sudo apt install docker-ce docker-ce-cli containerd.io
```
### Post install [:arrow_up:](#index)
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
### docker-compose [:arrow_up:](#index)
```bash
# !!! jq must be installed !!!
sudo curl -L https://github.com/docker/compose/releases/download/$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | jq .name -r)/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
```
```bash
sudo chmod +x /usr/local/bin/docker-compose
```
```bash
sudo ln -sf /usr/local/bin/docker-compose /usr/bin/docker-compose
```
### Copy From Container [:arrow_up:](#index)
```bash
sudo docker cp mysql:/was_impressions.sql.gz .
```

## List Container IPs [:arrow_up:](#index)
```bash
docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)
```

# PHP installation [:arrow_up:](#index)
Debian 10 (Buster)
#### PHP 7.4 [:arrow_up:](#index)
```bash
apt install gnupg2 -y
wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -

echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/php.list

sudo apt update
sudo apt upgrade

sudo apt install php7.4
sudo apt install php7.4-mysql php7.4-zip php7.4-curl php7.4-intl php-uuid php-amqp php-mongodb php7.4-sqlite3 php7.4-gd php7.4-soap php-pear php7.4-dev php7.4-mbstring php7.4-xml php7.4-cgi php7.4-xml php-xdebug php7.4-sqlite3
```

#### PHP 7.3 [:arrow_up:](#index)
```bash
# default is php7.3
sudo apt-get install php
sudo apt-get install php-zip php-curl php-intl php-uuid php-amqp php-mongodb php-sqlite3 php-mysql php-gd php-soap php-pear php-dev php-mbstring php-xml php-cgi php-xml php-dom php-xdebug sqlite php-sqlite3
```
```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get install php7.2
sudo apt-get install php7.2-zip php7.2-curl php7.2-intl php-uuid php-amqp php-mongodb php7.2-sqlite3 php7.2-mysql php7.2-gd php7.2-soap php-pear php7.2-dev php7.2-mbstring php7.2-xml php7.2-cgi php-xml php7.2-dom php7.2-xdebug php7.2-mysql sqlite php7.2-sqlite3
```
# [PHPUnit](https://phpunit.de/) [:arrow_up:](#index)
```bash
composer global require phpunit/phpunit
```

# **[PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)** [:arrow_up:](#index)
```
composer global require "squizlabs/php_codesniffer=*"
```

### **[phpcpd](https://github.com/sebastianbergmann/phpcpd)** [:arrow_up:](#index)
Copy/Paste Detector (CPD) for PHP code.
```bash
composer global require sebastian/phpcpd
```
#### Usage Example
```
$ phpcpd --fuzzy wordpress-4.9.8
phpcpd 4.1.0 by Sebastian Bergmann.

Found 66 clones with 3014 duplicated lines in 40 files:

 - /home/sb/wordpress-4.9.8/wp-includes/Requests/IRI.php:358-708 (350 lines) /home/sb/wordpress-4.9.8/wp-includes/SimplePie/IRI.php:404-754.
.
.
 - /home/sb/wordpress-4.9.8/wp-includes/SimplePie/File.php:133-144 (11 lines) /home/sb/wordpress-4.9.8/wp-includes/SimplePie/File.php:215-226
0.86% duplicated lines out of 349460 total lines of code.
Average size of duplication is 45 lines, largest clone has 350 of lines

Time: 1.79 seconds, Memory: 272.00MB

```
### **[PhpMetrics](https://github.com/phpmetrics/PhpMetrics)** [:arrow_up:](#index)
PhpMetrics provides metrics about PHP project and classes, with beautiful and readable HTML report.
```bash
# Globally
composer global require phpmetrics/phpmetrics
# For one project
composer require phpmetrics/phpmetrics
```
```bash
# Laravel
phpmetrics --report-html=myreport.html ./app
# Whole project
php ./vendor/bin/phpmetrics --report-html=myreport .
```


### **[PHPLOC](https://github.com/sebastianbergmann/phploc)** [:arrow_up:](#index)
A tool for quickly measuring the size and analyzing the structure of a PHP project.
```bash
composer global require phploc/phploc
```
#### Usage
```bash
phploc src
# e.g (laravel)
phploc ./app

phploc 4.0.0 by Sebastian Bergmann.

Directories                                          3
Files                                               10

Size
 Lines of Code (LOC)                             1882 Comment Lines of Code (CLOC)                     255 (13.55%) Non-Comment Lines of Code (NCLOC)               1627 (86.45%) . . .```
### [PHPMD - PHP Mess Detector](https://phpmd.org/documentation/index.html) [:arrow_up:](#index)
It takes a given PHP source code base and look for several potential problems within that source. These problems can be things like:

- Possible bugs
- Suboptimal code
- Overcomplicated expressions
- Unused parameters, methods, properties
```bash
composer global require phpmd/phpmd
```
#### Usage
`phpmd [filename|directory] [report format] [ruleset file]`
`phpmd PHP/Depend/DbusUI/ xml rulesets/codesize.xml`
while
`rulesets/codesize.xml`:
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<pmd version="0.0.1" timestamp="2009-12-19T22:17:18+01:00">
 <file name="/projects/pdepend/PHP/Depend/DbusUI/ResultPrinter.php"> <violation beginline="67" endline="224" rule="TooManyMethods" ruleset="Code Size Rules" package="PHP_Depend\DbusUI" class="PHP_Depend_DbusUI_ResultPrinter" priority="3"> This class has too many methods, consider refactoring it. </violation> </file></pmd>
```
### dd for PHP [:arrow_up:](#index)
```php
<?php
function dd($data) {
 highlight_string("<?php\n " . var_export($data, true) . "?>");
 echo '<script>document.getElementsByTagName("code")[0].getElementsByTagName("span")[1].remove();document.getElementsByTagName("code")[0].getElementsByTagName("span")[document.getElementsByTagName("code")[0].getElementsByTagName("span").length - 1].remove();</script>'; die();}
```
### PHP Elvis ?: and Null Coalescing ?? operators [:arrow_up:](#index)

|Expression         |echo ($x ?: 'hello')           |echo ($x ?? 'hello') |
|-------------------|-------------------------------|---------------------|
|$x = "";           |'hello'                        |""                   |
|$x = null;         |'hello'                        |'hello'              |
|$x;                |'hello'(Undefined variable: x) |'hello'              |
|$x = [];           |'hello'                        |[]                   |
|$x = ['a', 'b'];   |['a', 'b']                     |['a', 'b']           |
|$x = false;        |'hello'                        |false                |
|$x = true;         |true                           |true                 |
|$x = 1;            |1                              |1                    |
|$x = 0;            |'hello'                        |0                    |
|$x = -1;           |-1                             |-1                   |
|$x = '1';          |'1'                            |'1'                  |
|$x = '0';          |'hello'                        |'0'                  |
|$x = '-1';         |'-1'                           |'-1'                 |
|$x = 'random';     |'random'                       |'random'             |
|$x = new stdClass; |object(stdClass)               |object(stdClass)     |

### User Agent device [:arrow_up:](#index)
```bash
# mobile
/Mobile|iP(hone|od|ad)|Android|BlackBerry|IEMobile|Kindle|NetFront|Silk-Accelerated|(hpw|web)OS|Fennec|Minimo|Opera M(obi|ini)|Blazer|Dolfin|Dolphin|Skyfire|Zune/
```
```php
public static function GetDeviceType(string ua) {
string ret = "";// Check if user agent is a smart TV - http://goo.gl/FocDk
if (Regex.IsMatch(ua, @"GoogleTV|SmartTV|Internet.TV|NetCast|NETTV|AppleTV|boxee|Kylo|Roku|DLNADOC|CE\-HTML", RegexOptions.IgnoreCase)) {
 ret = "tv";} // Check if user agent is a TV Based Gaming Console
else if (Regex.IsMatch(ua, "Xbox|PLAYSTATION.3|Wii", RegexOptions.IgnoreCase)) {
 ret = "tv";} // Check if user agent is a Tablet
else if ((Regex.IsMatch(ua, "iP(a|ro)d", RegexOptions.IgnoreCase) || (Regex.IsMatch(ua, "tablet", RegexOptions.IgnoreCase)) && (!Regex.IsMatch(ua, "RX-34", RegexOptions.IgnoreCase)) || (Regex.IsMatch(ua, "FOLIO", RegexOptions.IgnoreCase)))) {
 ret = "tablet";} // Check if user agent is an Android Tablet
else if ((Regex.IsMatch(ua, "Linux", RegexOptions.IgnoreCase)) && (Regex.IsMatch(ua, "Android", RegexOptions.IgnoreCase)) && (!Regex.IsMatch(ua, "Fennec|mobi|HTC.Magic|HTCX06HT|Nexus.One|SC-02B|fone.945", RegexOptions.IgnoreCase))) {
 ret = "tablet";} // Check if user agent is a Kindle or Kindle Fire
else if ((Regex.IsMatch(ua, "Kindle", RegexOptions.IgnoreCase)) || (Regex.IsMatch(ua, "Mac.OS", RegexOptions.IgnoreCase)) && (Regex.IsMatch(ua, "Silk", RegexOptions.IgnoreCase))) {
 ret = "tablet";} // Check if user agent is a pre Android 3.0 Tablet
else if ((Regex.IsMatch(ua, @"GT-P10|SC-01C|SHW-M180S|SGH-T849|SCH-I800|SHW-M180L|SPH-P100|SGH-I987|zt180|HTC(.Flyer|\\_Flyer)|Sprint.ATP51|ViewPad7|pandigital(sprnova|nova)|Ideos.S7|Dell.Streak.7|Advent.Vega|A101IT|A70BHT|MID7015|Next2|nook", RegexOptions.IgnoreCase)) || (Regex.IsMatch(ua, "MB511", RegexOptions.IgnoreCase)) && (Regex.IsMatch(ua, "RUTEM", RegexOptions.IgnoreCase))) {
 ret = "tablet";} // Check if user agent is unique Mobile User Agent
else if ((Regex.IsMatch(ua, "BOLT|Fennec|Iris|Maemo|Minimo|Mobi|mowser|NetFront|Novarra|Prism|RX-34|Skyfire|Tear|XV6875|XV6975|Google.Wireless.Transcoder", RegexOptions.IgnoreCase))) {
 ret = "mobile";} // Check if user agent is an odd Opera User Agent - http://goo.gl/nK90K
else if ((Regex.IsMatch(ua, "Opera", RegexOptions.IgnoreCase)) && (Regex.IsMatch(ua, "Windows.NT.5", RegexOptions.IgnoreCase)) && (Regex.IsMatch(ua, @"HTC|Xda|Mini|Vario|SAMSUNG\-GT\-i8000|SAMSUNG\-SGH\-i9", RegexOptions.IgnoreCase))) {
 ret = "mobile";} // Check if user agent is Windows Desktop
else if ((Regex.IsMatch(ua, "Windows.(NT|XP|ME|9)")) && (!Regex.IsMatch(ua, "Phone", RegexOptions.IgnoreCase)) || (Regex.IsMatch(ua, "Win(9|.9|NT)", RegexOptions.IgnoreCase))) {
 ret = "desktop";} // Check if agent is Mac Desktop
else if ((Regex.IsMatch(ua, "Macintosh|PowerPC", RegexOptions.IgnoreCase)) && (!Regex.IsMatch(ua, "Silk", RegexOptions.IgnoreCase))) {
 ret = "desktop";} // Check if user agent is a Linux Desktop
else if ((Regex.IsMatch(ua, "Linux", RegexOptions.IgnoreCase)) && (Regex.IsMatch(ua, "X11", RegexOptions.IgnoreCase))) {
 ret = "desktop";} // Check if user agent is a Solaris, SunOS, BSD Desktop
else if ((Regex.IsMatch(ua, "Solaris|SunOS|BSD", RegexOptions.IgnoreCase))) {
 ret = "desktop";} // Check if user agent is a Desktop BOT/Crawler/Spider
else if ((Regex.IsMatch(ua, "Bot|Crawler|Spider|Yahoo|ia_archiver|Covario-IDS|findlinks|DataparkSearch|larbin|Mediapartners-Google|NG-Search|Snappy|Teoma|Jeeves|TinEye", RegexOptions.IgnoreCase)) && (!Regex.IsMatch(ua, "Mobile", RegexOptions.IgnoreCase))) {
 ret = "desktop";} // Otherwise assume it is a Mobile Device
else {
 ret = "mobile";}
 return ret;
}
```

# MySql [:arrow_up:](#index)
### MySql Export [:arrow_up:](#index)

```bash
mysqldump netwas was_impressions --where="created_at < '2019-10-06 16:00:00'" -u root -p | gzip > was_impressions.sql.gz
```
or
```bash
mysql -e "select * from was_impressions where created_at < '2019-05-29 00:00:00'" -u root -p netwas > was_impressions.sql
```
# Elasticsearch [:arrow_up:](#index)
### Elasticsearch Vm Max Map Count [:arrow_up:](#index)

```bash
sudo sysctl -w vm.max_map_count=262144
```
or
```bash
sudo nano /etc/sysctl.conf
```
and add

`vm.max_map_count=262144`

# Composer [:arrow_up:](#index)
### Composer installation [:arrow_up:](#index)
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
 >&2 echo 'ERROR: Invalid installer signature' rm composer-setup.php exit 1fi

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
 # The ServerName directive sets the request scheme, hostname and port that # the server uses to identify itself. This is used when creating # redirection URLs. In the context of virtual hosts, the ServerName # specifies what hostname must appear in the request's Host: header to # match this virtual host. For the default virtual host (this file) this # value is not decisive as it is used as a last resort host regardless. # However, you must set it for any further virtual host explicitly. #ServerName www.example.com
 ServerAdmin webmaster@example.dev ServerName example.dev ServerAlias www.example.dev DocumentRoot /var/www/html/example.dev/public_html
 # Available loglevels: trace8, ..., trace1, debug, info, notice, warn, # error, crit, alert, emerg. # It is also possible to configure the loglevel for particular # modules, e.g. # LogLevel info ssl:warn
 ErrorLog ${APACHE_LOG_DIR}/error.log CustomLog ${APACHE_LOG_DIR}/access.log combined
 # For most configuration files from conf-available/, which are # enabled or disabled at a global level, it is possible to # include a line for only one particular virtual host. For example the # following line enables the CGI configuration for this host only # after it has been globally disabled with "a2disconf". #Include conf-available/serve-cgi-bin.conf</VirtualHost>
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

# Nodjs [:arrow_up:](#index)
#### npm installation [:arrow_up:](#index)
```bash
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs
```
#### Remove node_modules (cache error) [:arrow_up:](#index)
```bash
sudo rm -rf node_modules
```
???
```bash
sudo apt-get install libpng-dev
```
### npm permission problem [:arrow_up:](#index)

```bash
sudo chown $USER:$USER -R $HOME/.npm
```
### globally installations permission error
```bash
sudo chown -R $USER:$USER /usr/lib/node_modules
```
# Postman [:arrow_up:](#index)
### Postman Pre-Requests [:arrow_up:](#index)
```bash
pm.request.headers.add({"key": "Accept", "value": "application/json"});
pm.request.headers.add({"key": "Content-Type", "value": "application/json"});
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
ln -s ./storage/app/public/uploads ./public/uploads
```
### Laravel on shared host .htaccess [:arrow_up:](#index)
```
<IfModule mod_rewrite.c>
 RewriteEngine On RewriteRule ^(.*)$ public/$1 [L]</IfModule>
```
### Laravel IDE helper [:arrow_up:](#index)
```bash
composer require --dev barryvdh/laravel-ide-helper
```
```php
# config/app.php
[
// ...
Barryvdh\LaravelIdeHelper\IdeHelperServiceProvider::class,
// ...
];
```
```bash
php artisan ide-helper:generate
```

### Laravel log regex [:arrow_up:](#index)
```bash
\.ERROR\:?.*$    # ERROR
\.WARNING\:?.*$  # WARNING
\.INFO\:?.*$     # INFO
```
# Git [:arrow_up:](#index)
#### Git global setup
```bash
git config --global user.name "john Doe"
git config --global user.email "email@website.com"
```
#### Create a new repository [:arrow_up:](#index)
```bash
git clone https://gitlab.com/user/project.git
cd laravel-tdd
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```
#### Push an existing folder [:arrow_up:](#index)
```bash
cd existing_folder
git init
git remote add origin https://gitlab.com/user/project.git
git add .
git commit -m "Initial commit"
git push -u origin master
```
#### Push an existing Git repository [:arrow_up:](#index)
```bash
cd existing_repo
git remote rename origin old-origin
git remote add origin https://gitlab.com/user/project.git
git push -u origin --all
git push -u origin --tags
```

## Git log [:arrow_up:](#index)
```bash
alias gl="git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

# PhpStorm [:arrow_up:](#index)

### Crack: [:arrow_up:](#index)

```bash
sudo nano /etc/hosts
```
```bash
0.0.0.0 account.jetbrains.com
```
[Patch file](http://idea.lanyus.com/jar)
Open
`/opt/PhpStorm/bin/phpstorm.vmoptions`
`/opt/PhpStorm/bin/phpstorm64.vmoptions`
and add
`-javaagent:/opt/PhpStorm/bin/JetbrainsIdesCrack.jar`
[Get a key](http://idea.lanyus.com/getkey)
[Servers](https://www.licensez.com/)

# VSCode [:arrow_up:](#index)

### Custom status bar with shortcuts
First install "Commands" extension by pressing `ctrl+p` and
```
ext install fabiospampinato.vscode-commands
```
then edit "settings.json" and add
```json
{
  "workbench.startupEditor": "newUntitledFile",
  "workbench.colorCustomizations": {
  "statusBar.background" : "#1A1A1A",  "statusBar.noFolderBackground" : "#212121",  "statusBar.debuggingBackground": "#263238"
 },  "commands.commands": [
 {  "text": "|",
  "command": "",
  "tooltip": "",
  "color": "black"
 }, {  "text": "$(file-directory)",
  "command": "workbench.view.explorer",
  "tooltip": "Explorer"
 }, {  "text": "$(file-code) New",
  "command": "workbench.action.files.newUntitledFile",
  "tooltip": "New file"
 }, {  "text": "$(checklist) Save",
  "command": "workbench.action.files.save",
  "tooltip": "Save file"
 }, {  "text": "|",
  "command": "",
  "tooltip": "",
  "color": "black"
 }, {  "text": "$(terminal)",
  "command": "workbench.action.terminal.focusAtIndex1",
  "tooltip": "Focus to terminal #1"
 }, {  "text": "$(markdown)",
  "command": "markdown.showPreviewToSide",
  "tooltip": "Open markdown preview",
  "filterFileRegex": ".*\\.md"
 }, {  "text": "Init",
  "command": "terminals.runTerminalByName",
  "arguments": ["init"],
  "tooltip": "Init the project"
 }, {  "text": "Serve",
  "command": "terminals.runTerminalByName",
  "arguments": ["serve"],
  "tooltip": "Serve the project"
 }, {  "text": "$(chevron-right)",
  "command": "workbench.action.showCommands",
  "tooltip": "Show commands"
 }, {  "text": "$(gear)",
  "command": "workbench.action.openGlobalSettings",
  "tooltip": "Settings"
 }, {  "text": "|",
  "command": "",
  "tooltip": "",
  "color": "black"
 }, {  "text": "$(triangle-right)",
  "command": "workbench.action.debug.start",
  "tooltip": "Start debugging",
  "color": "green"
 }, {  "text": "$(primitive-square)",
  "command": "workbench.action.debug.stop",
  "tooltip": "Stop debugging",
  "color": "red"
 }, {  "text": "|",
  "command": "",
  "tooltip": "",
  "color": "black"
 }, {  "text": "$(search)",
  "command": "workbench.view.search",
  "tooltip": "Search"
 }, {  "text": "$(repo-forked)",
  "command": "workbench.view.scm",
  "tooltip": "Source Control"
 }, {  "text": "$(bug)",
  "command": "workbench.view.debug",
  "tooltip": "Debug"
 }, {  "text": "$(package)",
  "command": "workbench.view.extensions",
  "tooltip": "Extensions"
 }, {  "text": "|",
  "command": "",
  "tooltip": "",
  "color": "black"
 }, {  "command": "commands.refresh",
  "text": "$(sync)",
  "tooltip": "Refresh commands",
  "color": "#FFCC00"
 } ]}
```
# VIM [:arrow_up:](#index)
[vim cheat sheet](https://vim.rtorr.com/)
```bash
# Delete all lines in a file
:1,$d
gg dG
```

# Linux [:arrow_up:](#index)
## Load other drives automatically on start up [:arrow_up:](#index)
```bash
sudo nano /etc/fstab
```
then
```bash
UUID=*** /media/user/D ntfs-3g defaults 0 0
```
or
```bash
/dev/sdb1 /media/user/D ext4 defaults 0 0
```

## Wifi deriver [:arrow_up:](#index)
### Lenovo 
##### option 1
```bash
lspci | grep -i wireless
# if any version of atheros
sudo apt install firmware-atheros synaptic
```
##### option 2:
[Qualcomm-Atheros-QCA9377-wireless-not-working-on-lenovo-with-Ubuntu](https://github.com/fnzeta/Qualcomm-Atheros-QCA9377-wireless-not-working-on-lenovo-with-Ubuntu/blob/master/README.md)

### ASUS Realtek RTL8821CE
#### [Realtek RTL8821CE Driver](https://github.com/tomaspinho/rtl8821ce)

## Bluetooth headsets problem [:arrow_up:](#index)

```
sudo apt-get install pulseaudio-module-bluetooth
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
Delete a rule
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
## Network restart Ubuntu [:arrow_up:](#index)
```bash
sudo /etc/init.d/networking restart
```
## Desktop icon [:arrow_up:](#index)
```bash
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
 <mime-type type="text/plain"> <glob pattern="*.md"/> <glob pattern="*.mkd"/> <glob pattern="*.markdown"/> </mime-type></mime-info>

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

Extract the downloaded fonts in `~/.fonts` directory into their own folder
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
## Colors in terminal [:arrow_up:](#index)
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

## SWAP size [:arrow_up:](#index)

|RAM Size |Swap Size (Without Hibernation)  |Swap size (With Hibernation) |
|---------|---------------------------------|-----------------------------|
|256MB    |256MB                            |512MB                        |
|512MB    |512MB                            |1GB                          |
|1GB      |1GB                              |2GB                          |
|2GB      |1GB                              |3GB                          |
|3GB      |2GB                              |5GB                          |
|4GB      |2GB                              |6GB                          |
|6GB      |2GB                              |8GB                          |
|8GB      |3GB                              |11GB                         |
|12GB     |3GB                              |15GB                         |
|16GB     |4GB                              |20GB                         |
|24GB     |5GB                              |29GB                         |
|32GB     |6GB                              |38GB                         |
|64GB     |8GB                              |72GB                         |
|128GB    |11GB                             |139GB                        |


## Upgrade only one package [:arrow_up:](#index)
```bash
sudo apt --only-upgrade install package
```

## Tmux [:arrow_up:](#index)
```bash
sudo apt install tmux
```
```bash
################# divide screen vertically #######################
ctrl + b then %
################# divide screen horizontally ####################
ctrl + b then "
################# switch windows ################################
ctrl + b then arrow keys
################# detach ########################################
ctrl + b then d
################# list screens ##################################
tmux ls
################# attach ########################################
tmux att -t [#]
################# Zoom to a part ###############################
ctrl + b then z
################# exit tmux ####################################
exit enter
```
## Copy Progress [:arrow_up:](#index)
```bash
alias pv='rsync --info=progress2'
```
## VLC [:arrow_up:](#index)
```bash
sudo apt install vlc
# Extra features
sudo apt install vlc-plugin-access-extra vlc-plugin-fluidsynth vlc-plugin-jack vlc-plugin-notify vlc-plugin-samba vlc-plugin-skins2 vlc-plugin-svg vlc-plugin-video-splitter vlc-plugin-visualization
```

## Custom gestures [:arrow_up:](#index)
[https://gitlab.com/cunidev/gestures](https://gitlab.com/cunidev/gestures)
[https://github.com/bulletmark/libinput-gestures](https://github.com/bulletmark/libinput-gestures)

### Installation [:arrow_up:](#index)
```bash
sudo gpasswd -a $USER input
sudo apt-get install xdotool wmctrl
sudo apt-get install libinput-tools
```
```bash
git clone https://github.com/bulletmark/libinput-gestures.git
cd libinput-gestures
sudo ./libinput-gestures-setup install
```
```bash
libinput-gestures-setup autostart
libinput-gestures-setup start
```

```bash
sudo nano ~/.config/libinput-gestures.conf
```
add
```
# change workspace
gesture swipe left 4 xdotool set_desktop 0
gesture swipe right 4 xdotool set_desktop 1
gesture swipe up 4 xdotool key ctrl+F8

# Show open windows
gesture swipe up 3 xdotool key ctrl+F9

# Show desktop
gesture pinch out 2 xdotool key ctrl+F12
```
then run
```bash
libinput-gestures-setup restart
```

### Debug [:arrow_up:](#index)
```bash
libinput-gestures -d
```

#### REMOVAL [:arrow_up:](#index)

```bash
libinput-gestures-setup stop
libinput-gestures-setup autostop
sudo libinput-gestures-setup uninstall
```

## Enpass browser sync problem [:arrow_up:](#index)
```bash
sudo apt install desktop-file-utils
sudo update-desktop-database
sudo update-mime-database /usr/share/mime
```

# Windows [:arrow_up:](#index)

### MBR to GPT [:arrow_up:](#index)
```bash
diskpart
list disk
select disk 0
clean
convert gpt
```
### Windows Enterprise Activation [:arrow_up:](#index)
```bash
slmgr /skms kms.digiboy.ir
slmgr /ato
```
