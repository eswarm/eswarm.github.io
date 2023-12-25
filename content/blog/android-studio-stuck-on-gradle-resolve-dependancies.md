+++
author = "Eswar Malla"
categories = ["blog", "android", "tools", "commands"]
date = 2016-04-08T15:18:00Z
description = ""
draft = false
slug = "android-studio-stuck-on-gradle-resolve-dependancies"
tags = ["blog", "android", "tools", "commands"]
title = "Android Studio stuck on 'Gradle: resolve dependancies'"

+++


Check all the dependencies, whether they are valid or not.

Or for a temporary fix, try offline mode.

> To enable this setting go to:Preferences -> GradleIn the right side options go down to "Global Gradle Settings" and check the "Offline work" box.

* Build from the command line to know the exact source of the problem

In windows

> gradlew.bat assembleDebug

In linux

> chmod +x gradlew./gradlew assembleDebug

* If nothing works, You can also try to delete all contents of folder C:\Users<Username>.gradle

