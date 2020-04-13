---
layout: post
title:  "QT [cute] for VESC_Tool on macOS"
author: gl
categories:
tags: [Technology]
image: https://res-2.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-7.27.10-PM.png
description: ""
rating: 
---

Over the years I have familiarized myself with many programming languages and learning new one not by choice but mere necessity.

I had come across QT a long while back as a great framework to build cross platform applications which are both powerful and delightful to look at, but then very recently started getting in depth when I had to use VESC - Vedders Electronic Speed Controller for a project of mine. VESC_Tool uses the creative common license for building an amazing cross-platform interface for configuring and to run experiments on the VESC hardware, it also doubles as telemetry monitor for real-time logging while plotting gorgeous graphs for the powerful motor controller.

The VESC_Tool has been offered as a compiled binary free of cost for Windows and Linux while the Android version is available at a small price of $1.99 on Google Play and the non play-store version can be downloaded directly from https://vesc-project.com/, amidst this the lack of a stable release for IOS and macOS has been haunting as the later has been my daily driver for well over 3 years now, so I decided to build one.

The source code is distributed under GPL-v3 license and available at https://github.com/vedderb/vesc_tool, so lets start there by cloning it under our $HOME directory

```bash
git clone https://github.com/vedderb/vesc_tool
```
Once we comb through the top level files we can see that it contains ".qrc" files which symbolizes that project uses QT framework and going through the automated build file of Linux and Mac also iterates the same. The tool can be built using static library of QT but will start from scratch and cover all the basics just to sure.

Requirements:
QT

Although QT can be downloaded using the unified tool available from the official website, in this exercise we will  Homebrew it.!!

Note : If you don't have Homebrew in your macOS follow instruction at https://brew.sh/

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
Assuming you have got Homebrew installed successfully lets start by opening the terminal and brewing the latest version of qt [in our case qt 5.14.1]

```bash
brew install qt
```

qt is keg-only, which means it was not symlinked into /usr/local,
because Qt 5 has CMake issues when linked.

Once completed we need to  symlink it by executing below command 

```bash
export PATH="/usr/local/opt/qt/bin:$PATH"
```
At this point we can just rewire the path towards the qt libraries and be able to start the vesc-tool by building it with dynamic libraries.

Now move to the vesc_tool folder and lets create a build file for building with dynamic qt libraries.

```bash
cd ~/vesc_tool
nano build_macos_original_only
```

Add the following lines...

```bash
#!/bin/bash
rm -rf build/macos/*
qmake -config release "CONFIG += release_macos build_original"
make clean
make -j8
rm -rf build/macos/obj
cd build/macos
```
Lets make the file executable run the build from the root folder

```bash
chmod +x ./build_macos_original_only
./build_macos_original_only
```

This will take a while...If things go as planned without spitting out any errors, you will have a fresh binary file in the ~/vesc_tool/build/macos/ folder with name vesc_tool_[version].app
now you can run the vesc_tool in your macOS simply calling it from terminal.

```bash
open ~/vesc_tool/build/macos/vesc_tool_2.03.app
```

![](https://res-4.cloudinary.com/htlffy4aw/image/upload/q_auto/v1/ghost-blog-images/Screenshot-2020-03-30-at-6.13.23-PM.png)

In the next post, I will cover how to build the same without using terminal.

References and Bibliography:
https://github.com/vedderb/vesc_tool
https://github.com/rpasichnyk/vesc_tool/
https://retifrav.github.io/blog/2018/02/17/build-qt-statically/
