+++
author = "Eswar Malla"
categories = ["PI", "raspberry", "Raspberry PI", "Raspberry PI 4"]
date = 2021-02-28T05:38:41Z
description = ""
draft = false
image = "/images/2021/02/raspberry.png"
slug = "configuring-raspberry-pi-4-without-sd-card-reader-or-external-monitor"
summary = "Configuring  and accessing Raspberry PI(4) without SD Card reader or external monitor "
tags = ["PI", "raspberry", "Raspberry PI", "Raspberry PI 4"]
title = "Configuring  and accessing Raspberry PI(4) without SD Card reader or external monitor"

+++


You have a new Raspberry PI, but for some odd reason do not have access to an external monitor to spare or a SD Card reader, fret not, we can still get you up and running. 

What you will need.

* Raspberry PI(of course). 
* Android Phone which can read SD Cards.

I did not have access to an SD card reader since the mac book "pro" decided that true "pros" do not need any external devices. Had to figure a way out.

* Load the SD Card into an Android phone.Download the app PI SDCard imager(https://play.google.com/store/apps/details?id=com.redrobe.raspicardimager&hl=en_IN&gl=US).
* Inside the app select the SD card folder and the image to burn.I was never able to burn the Pi desktop image(3 GB) so I resorted to burning the PI image lite(without desktop), the app is very finicky and can fail multiple times, your mileage may vary. 


After the image is written on to the SD Card, we need to configure the image to accept SSH connections over USB first.


* Go to the root folder of the SD Card(I just copied the files made modifications and copied them back)

* Open config.txt and append this at the end.

> dtoverlay=dwc2

* Open cmdline.txt and append this to the command that is present, make sure it is on the same line.

> modules-load=dwc2,g_ether

* Create a new file called ssh and copy the same into the root folder.

We are good to go access the pi over ssh

Now place the SD Card inside the PI, connect the PI over USB and launch a terminal. Depending on which OS you are on the steps would vary. For me this is enough.

> ssh pi@raspberry.local

Now enter the default password(raspberry) to step into SSH.

If you are happy with this access you can stop now, but since PI has WiFi it would be a shame not to enable that. 

Follow the steps here. 

https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md

After you configure WiFi you can have access to any packages you want. 

Since I installed PI Lite initially, I did this to install PI Desktop. 

> sudo apt-get update && sudo apt-get -y dist-upgrade && sudo apt-get install raspberrypi-ui-mods

Once you have the desktop, you can install VNC to access your PI from within the local network. Follow the steps here. Ignore that steps about accessing from cloud, most likely you will not need it. 

https://www.raspberrypi.org/documentation/remote-access/vnc/

And that't it, now you have access to the PI from your machine and you can configure it as you deem fit. 


Sources : https://www.thepolyglotdeveloper.com/2016/06/connect-raspberry-pi-zero-usb-cable-ssh/
https://www.raspberrypi.org/documentation/remote-access/ssh/







