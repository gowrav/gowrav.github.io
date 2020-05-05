---
layout: post
title:  "CD with Travis and Github"
author: gl
categories:
tags: [Technology]
image: 
description: ""
rating: 
---
# Rant
One thing that is missing in VESC github repo and the download is the build revisions, agreed its an open source project with git version control that anyone can build on their own by chceking out the version that they are interested in. Still, it feels like an essential feature for a non tech enthusiast would need.

# Solution
So this post is about making an integration with Travis Ci/CD for Continous Deployment and Release it on Github.
This is primarily focussed on making a release that works for macOS.
One thing that I observe is lack of h/w computing resources with developers to make releases to all possible architectures. So I decided to make this work by using Xcode library availbale in Travis macOS environment.

ALl the post highlights are implemented in this github repo
https://github.com/gowrav-com/mak_vesc_tool



# References and Bibliography:
https://github.com/vedderb/vesc_tool
