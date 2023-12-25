+++
author = "Eswar Malla"
categories = ["blog", "android", "tools", "commands"]
date = 2016-04-18T15:14:00Z
description = ""
draft = false
slug = "set-date-and-time-from-adb"
tags = ["blog", "android", "tools", "commands"]
title = "Set date and time from adb"

+++


```

adb shell date -s YYYYMMDD.HHmmss adb shell date -s 20141020.165800

adb shell date -s 20120423.130000 adb shell 'su 0 date -s YYYYMMDD.HHmmss'


```



