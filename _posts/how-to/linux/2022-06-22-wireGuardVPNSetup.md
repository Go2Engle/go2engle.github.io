---
title: Wireguard VPN client setup   
date: 2022-06-22
categories: [How-to, Linux]
tags: [wireguard,vpn,ubuntu]     # TAG names should always be lowercase
---

## Overview

This guide will walk you through setting up Wireguard client on Ubuntu along with adding a toggle to your gnome interface. I will assume you already have a wireguard VPN server running elsewhere along with your wireguard client conf file.

## Installing and running Wireguard

1. Install wireguard.
```shell
sudo apt install wireguard
````

2. Create a `wg0.conf` file in `/etc/wireguard` and paste your wireguard client conf in this file. CTRL + X to save.
```shell
sudo nano /etc/wireguard/wg0.conf
```

At this point wireguard is now installed and configured you can start and stop wireguard with either of the below commands.
```shell
#start via service
sudo systemctl start wg-quick@wg0.service
#start via wg tool
sudo wg-quick up wg0

#stop via service
sudo systemctl stop wg-quick@wg0.service
#stop via wg tool
sudo wg-quick down wg0
```

## Enable and disable Wireguard via gnome shell extension

1. Enable wireguard-indicator extension. [LINK](https://extensions.gnome.org/extension/3612/wireguard-indicator/)

2. Go to the wireguard-indicator settings and modify the name of the first service. Make sure the service is set to `wg-quick@wg0.service` and click Ok.

3. Delete the second service