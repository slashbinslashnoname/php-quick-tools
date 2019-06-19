# Quick Tools for PHP on OSX

Installing PHP on OSx can be tricky.

These are my best shell scripts I use everytime I need to use php. I've found them online, so if you want to send a DMCA notice, you can go here : http://nowhere.com/

## Installing Brew

See https://brew.sh

## Installing xcode 

``
xcode-select --install
brew upgrade
``

## Installing multiple versions of php 

```
versions="php70 php71 php72 php73"
for version in $versions; do
    brew install $version
    brew install $version-xdebug
    brew unlink $version
done

```



## Edit Apache to use the right php version


To enable PHP in Apache add the following to httpd.conf and restart Apache:
    LoadModule php7_module /usr/local/opt/php/lib/httpd/modules/libphp7.so

    <FilesMatch \.php$>
        SetHandler application/x-httpd-php
    </FilesMatch>

Finally, check DirectoryIndex includes index.php
    DirectoryIndex index.php index.html

The php.ini and php-fpm.ini file can be found in:
    /usr/local/etc/php/7.3/

To have launchd start php now and restart at login:
  brew services start php
Or, if you don't want/need a background service you can just run:
  php-fpm

