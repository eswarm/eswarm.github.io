+++
author = "Eswar Malla"
date = 2016-09-16T15:16:00Z
description = ""
draft = false
slug = "recover-a-nexus-9-from-a-corrupt-ota"
title = "Recover a Nexus 9 from a corrupt OTA"

+++


This guide is on a Windows machine, you can follow most of it and adapt it for other operating systems though.

Before you do this make sure you have the drivers for adb, fastboot and  usb installed.

On Windows PC:

Right click on the Windows icon in the lower left corner of your screen and click Command Prompt.

Right click on the Windows icon in the lower left corner of your screen and click Device Manager.

On the Nexus 9:

Boot the Nexus 9 into HBOOT Mode. This can be done by pressing and holding both Power and Volume Down simultaneously.

Now switch to Fastboot Mode by tapping Volume Down until FASTBOOT is highlighted, then tap Power once.

At this point do a test to see if drivers are properly installed in the PC. Attach the USB cable between the PC and the Nexus 9. Device Manager should now show an entry of Android Phone with a sub-entry of Android Bootloader Interface.

In the command prompt on the PC from step 2, enter the command fastboot devices. If you see a response with the serial number of your Nexus 9, then all is good and proceed. If you do not see this then further work is required in the PC to get the required drivers installed, so do not proceed further and ask for assistance.

Remove the USB cable between the PC and the Nexus 9.

Tap Volume Down until HBOOT is highlighted, then tap Power to go back to HBOOT mode.

Then tap Volume Down until RECOVERY is highlighted, then tap Power once to select it.

After a few seconds you will see the Google logo followed by a green android on his back with “No command” underneath. Press and hold Power, then tap Volume Up once, then release Power.

NOTE: If your device starts rebooting at this point, your only recourse is to contact your place of purchase about a warranty replacement or repair.

You are now on the Android Recovery screen. On the third line at the top of the screen you will see something that looks like this:

6.0.1 / MOB30I / 2756745 (or)LFW73WThe 6 digit one(M0B30I) is your current Build Number. Make note of this as the Rescue OTA you need corresponds to this one or a more recent one. (NOTE:        You    cannot install an older one than your current Build Number.)

Tap Volume Down until the entry “Wipe cache partition” is highlighted, then tap Power to select it. Tap Volume Down once to highlight Yes, then tap Power again to start it.

When this is complete, tap Volume Down until the entry “Apply Update from ADB” is highlighted, then tap Power to select it. You Nexus 9 is now waiting to receive the OTA file.

Attach the USB cable between the PC and the Nexus 9. Device Manager should now show an entry of Android Device with a sub-entry of Android Composite ADB Interface.

In the command prompt on the PC from step 2, enter the command adb devices. If you see a response with the serial number of your Nexus 9, then all is good and proceed. If you do not see this then further work is required in the PC to get the required drivers installed. On windows you can do this to update the driver

Device Manager -> Go to volantis -> Right Click ->  Update Driver > Browse > Pick device > Android > "Android ADB interface"  (Ignore the warning.)

On Windows PC:

On your PC, create the folder c:\MyNexus

Download the OTA for the current Build Number of your Nexus 9 from here. (NOTE: Be sure to select the correct Nexus 9 group when you download the Rescue OTA – volantis is for the WiFi only Nexus 9, and volantisg is for the LTE or Mobile Nexus 9, i.e. the one with a SIM slot. If your current Build Number is not listed, use the first one in the list for your device model.)

When the download finishes, click on “Open Folder” at the bottom of the browser window. This will open Windows File Explorer. Right click on the highlighted file that was just downloaded, click Cut, then select the folder c:\MyNexus, right click again and click Paste to move the OTA zip file into c:\MyNexus.

If the Nexus 9 Apply Update from ADB timed out (step 13), then re-initiate it.

Enter a command similar to the following, but the highlighted filename will be the one you pasted into c:\MyNexus in step 17 (don’t forget the .zip extension in the command):

Nexus 9 (WiFi only)

```
adb sideload c:\MyNexus\volantis-ota-nrd90r-7c417d20.zip

```

Nexus 9 (Mobile)

```
adb sideload c:\MyNexus\volantisg-ota-mob31e-9a2b3565.zip

```

1. Progress messages should now appear on both the PC and the Nexus 9. If there are any errors, do not proceed further and ask for assistance.

On the Nexus 9:

When the update finishes the line “Reboot system now” should be highlighted. Tap power once to initiate a reboot.

After the reboot, your Nexus 9 should be back in operation.

Credit : Shamelessly copied from here, [https://drive.google.com/file/d/0Bz6x7k-VkpUJbGlQenRjM2hUMnM/view](https://drive.google.com/file/d/0Bz6x7k-VkpUJbGlQenRjM2hUMnM/view)

