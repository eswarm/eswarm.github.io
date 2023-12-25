+++
author = "Eswar Malla"
categories = ["blog", "beaglebone", "hardware", "somabot"]
date = 2016-05-04T15:10:00Z
description = ""
draft = false
slug = "somabot"
tags = ["blog", "beaglebone", "hardware", "somabot"]
title = "Somabot"

+++


{{< figure src="http://img.youtube.com/vi/SUPC4OL6UD4/0.jpg" >}}

The hardware interfacing is based on libmraa. You can use this on beaglebone black, Raspberry PI or the intel edison/galileo.

Just select the ingredients in the settings, and the right recipes are populated for generating your cocktails automatically.

The control software is a webserver you can access from any browser. Built to be responsive, so you can use it either on your mobile or desktop.

{{< figure src="/images/2020/05/home.png" >}}

{{< figure src="/images/2020/05/home2.png" >}}

{{< figure src="/images/2020/05/settings.png" >}}

If you want to add new recipes, just add new ones to the recipes.json, and the ingredients to ingredients.json they will be populated automatically.

## How to run the software.

### Prerequistes.

#### For Intel Edison and Intel Galileo

If you are using the standard images should work out of the box.

#### For Beaglebone.

Get the latest beaglebone debian distribution from

[http://beagleboard.org/latest-images](http://beagleboard.org/latest-images)

Install the following dependencies,

```
sudo apt-get install git build-essential swig3.0 python-dev nodejs-dev cmake
Build and Install mraa
libmraa is not in apt so we’ll have to compile it from source. Don’t worry, it’s easy:
git clone https://github.com/intel-iot-devkit/mraa.git
mkdir mraa/build && cd $_
cmake .. -DBUILDSWIGNODE=OFF
make
make install
Cd

```

```
bash sudo ln -s <your install prefix, e.g. /usr>/lib/python2.7/site-packages/* /usr/lib/python2.7/dist-packages 

```

I am not sure if I got the steps right, but the main reference is this.

[http://iotdk.intel.com/docs/master/mraa/building.html](http://iotdk.intel.com/docs/master/mraa/building.html)

And this

[https://learn.sparkfun.com/tutorials/installing-libmraa-on-ubilinux-for-edison](https://learn.sparkfun.com/tutorials/installing-libmraa-on-ubilinux-for-edison)

#### For Raspberry PI look here.

[http://www.elec-tron.org/?p=996](http://www.elec-tron.org/?p=996)

Once you got libmraa installed. Test using blink.py to check whether your GPIO pins are working properly or not.

cd into the somabot repo and do

```
pip install flask
python app.py

```

This will start your server. Access the web server through the ip address on which you are running.

