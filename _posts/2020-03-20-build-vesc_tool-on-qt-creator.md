---
layout: post
title:  "Build VESC_Tool on QT Creator"
author: gl
categories:
tags: [Technology]
image: https://res-5.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-7.28.01-PM.png
description: ""
rating:
---

This is an alternate flow for QT build of VESC_Tool for macOS shown here https://gowrav.com/qt-for-vesc-on-macos/ but without terminal

The source code can be obtained here https://github.com/vedderb/vesc_tool and one can download the project as zip file from github directly by following this link https://codeload.github.com/vedderb/vesc_tool/zip/master.
Extract the files into the home directory under the folder vesc_tool

You can install the latest version of QT framework by using the QT unified installer for macOS available here
http://download.qt.io/official_releases/online_installers/qt-unified-mac-x64-online.dmg
SignUp/SignIn with your QT credentials and use the appropriate license [I am using opensource license].

![](https://res-5.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-5.31.09-PM.png)


By default the location of installation is user home folder i.e $HOME/QT/
Next  up the components, choose the stable release version and install all  the packages/modules under v5.12.7 along side the Developer and Design  Tools.

![](https://res-3.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-5.34.32-PM.png)

This will take a long time to download and will occupy plenty of your disk space.

Once  the installation is done we can verify the components present by  opening the folder structure under $HOME folder, make sure you have qt  v5.12.7 inside it.

![](https://res-3.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-5.40.03-PM.png)

Now start QT creator from the finder and open the vesc_tool.pro project file under the extracted folder using File > Open File or Project...

![](https://res-1.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-7.07.33-PM.png)

Configure project in the Projects Tab while selecting only the necessary Kits, in this case [Desktop Qt 5.12.7 clang 64bit] and hit configure.

![](https://res-1.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Untitled.png)

The project is built and Run using the UI button at the bottom left corner of the IDE.

![](https://res-5.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-7.20.32-PM.png)

This will take 5 minutes and once Successful, the VESC_Tool will open up.!

![](https://res-5.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-7.20.42-PM.png)


