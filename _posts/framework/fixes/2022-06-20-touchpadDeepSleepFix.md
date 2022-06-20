---
title: Touchpad issues after deep sleep on PopOS 22.04
date: 2022-06-20
categories: [Framework, fixes]
tags: [framework,ubuntu,fixes]     # TAG names should always be lowercase
---


I just recently installed PopOS 22.04 and everything was running great! I got deep sleep working correctly, fingerprint reader working, and everything was fine until the laptop awoke from sleep. I noticed my mouse was way touchier and gestures were no longer working. After a bit of combing through the framework forums I stumbled along [this post](https://community.frame.work/t/ubuntu-21-04-trackpad-issues-when-waking-from-deep-sleep/10151/3). 

TLDR you just need to go into the BRIOS and disable `PS/2 emulation`.