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
versions="php56 php70 php71 php72 php73"
for version in $versions; do
    brew install $version --with-fpm
    brew install $version-xdebug
    brew unlink $version
done

```

