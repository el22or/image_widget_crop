ImageWidgetCrop module
======================

[![Build Status](https://travis-ci.org/woprrr/image_widget_crop.svg?branch=8.x-1.x)](https://travis-ci.org/woprrr/image_widget_crop)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/woprrr/image_widget_crop/badges/quality-score.png?b=8.x-1.x)](https://scrutinizer-ci.com/g/woprrr/image_widget_crop/?branch=8.x-1.x)

Provides an interface for using the features of the [Crop API]. Module is still 
under heavy development.

[Crop API]: https://github.com/drupal-media/crop
 
Requirements
------------

* GMP extension.

Configuration
-------------

* Create a Crop Type (`admin/structure/crop`)
* Create an ImageStyle 
    * add one ImageWidget Manual crop effect, using your Crop Type (to apply 
      your crop selection).
* Create an Image field.
* In its form display, at `admin/structure/types/manage/page/form-display`:
    * set the widget for your field to Image Widget crop 
    * at select your image style in the Crop settings list. You can configure 
      the widget to create different crops on each ImageStyle. For example, if 
      you have an editorial site, you need to display an image on different 
      places. With this option, you can set an optimal crop zone for each of the
      image styles applied to the image
* Set the display formatter Image and choose your image style.
* Go add an image with your widget and crop your picture.

Technical details
-----------------

### Installation of the GMP extension
#### Linux (Debian / Ubuntu / Mint)

* Just use the standard packaging commands 
 ```bash
sudo apt-get install libgmp-dev
sudo apt-get install php5-gmp
sudo service apache2 reload
```

#### MacOS X

* Install gmp on your system `brew install gmp`
* Run `php --version` to check which version of PHP you have.
* [Download](http://www.php.net/releases/) that version of PHP somewhere on your system.
* Run `phpize`, then compile it with
```bash
cd php-5.5.21/ext/gmp
phpize
./configure
make
make install
```
* Locate your php.ini file `php -i | grep "Loaded Configuration File"`
* Add the following to your php.ini
```ini
extension="gmp.so"
```
* Restart Apache
