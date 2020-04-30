---
layout: post
title:  "TimeLapse Photography with Arducam Bluetooth Android"
author: gl
categories:
tags: [Technology]
image: https://github.com/gowrav-com/mycam_bt_arducam_android/raw/master/sampleimages/2020-04-19_15%2017%2042-ANIMATION.gif
description: "A less than a hobby project for the enthusiasts of lights and shadows"
rating: 
---

This was less than a hobby project but was an outcome of mere spur of the week inspiration to do something in corona time with what i had at my old office space., so I brought the stuff.

Much to my amusement there were lot of great things in the stuff and I mean "were" as in they have become utterly outdated or just out lost.

## Things which doesn't matter any more.

#### The NTC Next Thing Chip
I spent may be 3 hours on this thing to see if I can get something done as this had an internal eeprom / flash memory for me to use as a small interpreter for the arduino gathering data out of an arducam or even a direct interface to the arducam itself. scrolling through the vastness of internet to find obscure source of hope to give life to NTC 
  * [Flash CHIP Firmware](http://chip.jfpossibilities.com/docs/chip.html#prepare-chip-for-flashing Flash CHIP Firmware)
  * [Archieved Pages](http://web.archive.org/web/20180918213953/https://bbs.nextthing.co/t/flashing-upcoming-fixed-images-without-the-chrome-flasher/11304/41)
  * [Sunny Page for Flashing CHIP](https://yoursunny.com/t/2018/CHIP-flash-offline/)

even when I did find courage to flash the CHIP by installing all the required tools the "sun" (pun intended) quickly set on the scheme of things as the board seemed to have a broken USB connector... I know I know that I have few other than this piece but thats where I drew the line and ended it.

#### RaspberryPI or Orange PI or Something...
Way too much work for project this scale .. more like way too much power...!! no thanks

#### [Link It One](https://docs.labs.mediatek.com/resource/linkit-one/en/getting-started)
more like no linking possible , seems Mediatek just decided to silently abondon [support for macOS](https://docs.labs.mediatek.com/resource/linkit-one/en/getting-started/get-started-on-os-x/install-the-arduino-ide-and-linkit-one-sdk-on-os-x) since the last supported driver is not compatible in macOS Catalina anymore..!! 

#### [Arducam shield v2 / Rev2](https://www.arducam.com/docs/spi-cameras-for-arduino/hardware/arducam-shield-v2/)
This was my original plan that I would use a 5MP camera and capture the timelapse of seed germination over 15day quarantine and put it on this blog, and as you can see thats not what happened., first up I wasted couplpe of days figuring out what was wrong with the configuration for not taking a picture in [5mp](https://www.arducam.com/product/5-mega-pixel-camera-module-ov5642-1080p-jpeg-output/) and transfering it to the MBP (Mac Book Pro) only to come to terms with the fact that I was using a RevC Arducam and Not a Rev3

#### [Arducam RevC](https://www.arducam.com/arducam-rev-c-plus-shield-released/)
Ok then how about RevC, yeah thats why it wasn't working in the first place., the buffer memory i.e FIFO on this thing is 512KB while to take a 5MP image I need you guessed it way more than 512KB., so that was not gonna happen. so that dropped quickly although I took some shots when I got it working with the Arduino Mega 2560 which I had bought for this sole purpose. It wasn't the way I wanted., the buffer on FIFO started to erupt with every shot even when put on 320x240 mode that to jpeg for some reason and then I had a light bulb moment how about I capture the data from the LCD?? as that was working fine.,
This is how it works
![Buffering and Displaying on LCD](https://www.arducam.com/wp-content/uploads/2012/09/ArduCAM.gif)
I did my research and here are some interesting facts the [bitmap RGB565](https://en.wikipedia.org/wiki/BMP_file_format) formatted image is used on the LCD and successfully implemented the idea only to have sub par images and that to fringed edges.
![Images Are Missing on this one]()

so what lets move on to the next option..
#### [Arducam Mini](https://www.arducam.com/product/arducam-2mp-spi-camera-b0067-arduino/)
Ok why mini ? you ask ?., lets just try whats possible with a 2MP camera on the ArduMini to see some light..
![Arducam Mini](https://www.arducam.com/wp-content/uploads/2019/01/b0067-2.jpg)

##### hook up guide
well I am no master of hookup however I do have few tricks up my sleve when it comes to it ;)
![Arducam Mini](https://www.arducam.com/wp-content/uploads/2019/01/B0067-1-2-160x160.jpg)
So it was pretty basic as you can see and I used Arduino Uno to get the job done.
![Arducam Mini Interface with Arduino Uno](https://raw.githubusercontent.com/gowrav-com/mycam_bt_arducam_android/master/sampleimages/IMG_20200419_150250.jpg)
For the detailed guide on the programming let me just point you to the tutorials and documentation on [Arducam Github Repo](https://github.com/ArduCAM/Arduino)
this involves largely running the example program and configuring the C-Files to suit your board of choice which in this case was arducam mini, take a snap on the request code via UART interface and transmit taken pic on to the system via UART.
After initial trials with Arduino-----UART------MBP HW-UART interfacing, I rigged up the HC-05 bluettoth to stream (using it very lightly here) data to the Android Smartphone for display and storage purposes.
![My BT Cam on My Window Sil](https://raw.githubusercontent.com/gowrav-com/mycam_bt_arducam_android/master/sampleimages/IMG_20200419_150237.jpg)

![Android Screenshot of the App](https://raw.githubusercontent.com/gowrav-com/mycam_bt_arducam_android/master/sampleimages/Screenshot_20200419-150230.png)

It has its bugs and issues due to very poorly written code and poorly configured hardware., but it does the job Well..ocasionally !!!

 * UART keeps disconnecting [Solved this with reconnecting loop in Android]
 * Range is limited [atleast for my purpose which is > 10Feet]
 * Image is inherently lack resolution for AstroPhotography
 * Code glareness compensation is poor for capturing the seed germination through a glass jar..! yikes..

So if you want to continue the journey or hack is further here is the source for you to clone, fork or download.
[Source Code for My Cam Bt Arducam Android](https://github.com/gowrav-com/mycam_bt_arducam_android)
[Arduino Code and Libraries](https://github.com/gowrav-com/mycam_bt_arducam_android/tree/master/ArduinoCode)
Last but not the least I took some nice pics for the rememberance and Google photos did its job of stitching the pieces into a nice GIF [pronounced 'Jh'--'efff']

![Gif of the sun's motion in the sky](https://github.com/gowrav-com/mycam_bt_arducam_android/raw/master/sampleimages/2020-04-19_15%2017%2042-ANIMATION.gif)

![My guitar posing](https://raw.githubusercontent.com/gowrav-com/mycam_bt_arducam_android/master/sampleimages/guitarcloudy.jpg)

![Outdoor Image for White balance adjustment](https://raw.githubusercontent.com/gowrav-com/mycam_bt_arducam_android/master/sampleimages/2020-04-19_14%2047%2000.jpg)


#### Repos for reference:
 * [https://github.com/ArduCAM/Arduino](https://github.com/ArduCAM/Arduino)
 * [https://github.com/douglasjunior/AndroidBluetoothLibrary](https://github.com/douglasjunior/AndroidBluetoothLibrary)
 * [http://chip.jfpossibilities.com/docs/index.html](http://chip.jfpossibilities.com/docs/index.html)
 * [https://www.robotshop.com/media/files/pdf2/arducam_camera_shield_software_application_note.pdf](https://www.robotshop.com/media/files/pdf2/arducam_camera_shield_software_application_note.pdf)
  
