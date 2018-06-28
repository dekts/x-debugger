# x-debugger
Install x-debugger for debug your different languages code at single platform

### Ubuntu 16.04, php 7.0
sudo apt-get install php-xdebug

### Ubuntu 14.04, php 5.6 
sudo apt-get install php5-xdebug

### Then after edit your xdebug.ini
* __Your xdebug.ini paths should look like this__
  * Ubuntu /etc/php/7.1/mods-available/xdebug.ini
* You can run locate *xdebug.ini to find xdebug.ini file location
* Add below lines without modifying exiting lines

```$xslt
xdebug.remote_enable = 1
xdebug.remote_port = 9000
xdebug.idekey = PHPSTORM
xdebug.show_error_trace = 1
xdebug.remote_autostart = 0
xdebug.file_link_format = phpstorm://open?%f:%l
```

* Above configs are bare minimum, read all options [here](https://xdebug.org/docs/all_settings)
* Restart the apache server to reflect changes

```$xslt
# Ubuntu
sudo service apache2 restart
```

## Configure phpStorm

* Go through - Settings >> Languages & Frameworks >> PHP >> Debug
* Check that 'Debug port' is the same you have in your xdebug.ini. In our case it was 9000.
* Save and close the Settings Dialog
* Start debugging
* Create some breakpoints in your project
* Make sure those breakpoints gets executed when your visit your virtual host in browser.
* Start listener by clicking on the telephone telephone_receiver button on top toolbar
* If you can't find telephone button; then go through menus - Run -> Start listening for PHP Debug Connections
* In your browser access your project url like this

```$xslt
http://localdomain.test/?XDEBUG_SESSION_START=1
```
* OR use [bookmarks](https://www.jetbrains.com/phpstorm/marklets/)
* OR use [this](https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc?hl=en) chrome extension
* You should see a popup window in PhpStorm , click Accept connection
* Done, enjoy debugging !!!

## Disable xdebug (Ubuntu)
```$xslt
sudo phpdismod xdebug
```

## Enable xdebug back (Ubuntu)
```$xslt
sudo phpenmod xdebug
```

## Disable xdebug for commandline only (Ubuntu)
```$xslt
sudo phpdismod -s cli xdebug
```

# Troubleshooting
* Try to change the port to something else, for example 18000
* Enable Break at first line in phpStorm php debug settings
* Set xdebug.remote_autostart to 1 if you don't want to bother with browser extensions
