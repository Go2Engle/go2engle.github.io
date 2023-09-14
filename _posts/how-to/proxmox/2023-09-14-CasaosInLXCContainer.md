---
title:  Setting up CasaOS in an LXC Container
date: 2023-09-14
categories: [How-to, Proxmox]
tags: [docker,LXC,container,proxmox,howto,casaos]     # TAG names should always be lowercase
---

In a previous blog post, we discussed how to create an unprivileged LXC container in Proxmox using the web interface and enabling KeyCTL support. If you haven't followed that guide yet, make sure to check it out here: [Creating an Unprivileged LXC Container in Proxmox via the UI with KeyCTL Support](https://go2engle.com/posts/UnprivilegedLXCContainerDocker/).

Now, with your unprivileged LXC container ready, let's explore how to set up CasaOS, a powerful home server solution, inside the container.

## Prerequisites

Before you begin, make sure you have the following:

1. An unprivileged LXC container created in Proxmox following the instructions from the previous blog post.
2. Administrative access to your LXC container.
3. Internet access from within the container (ensure your container is connected to the network).

## Step 1: Install Curl

Inside your LXC container, open a terminal and install `curl` if it's not already installed. You can do this by running the following command:

```shell
apt update
apt install curl
```

## Step 2: Install CasaOS

Once `curl` is installed, you can use it to download and run the CasaOS installation script. Run the following command:

```shell
curl -fsSL https://get.casaos.io | sudo bash
```

This command will fetch the CasaOS installation script from the official source and execute it. Follow the prompts and instructions provided by the installer to complete the setup process.

Please note that CasaOS may require specific hardware and configuration options. Make sure to consult the CasaOS documentation for any hardware or compatibility considerations.

## Step 3: Access CasaOS

After the installation is complete, CasaOS should be up and running inside your LXC container. You can access the CasaOS web interface by opening a web browser and navigating to the IP address or hostname of your LXC container.


## Conclusion

Setting up CasaOS in an LXC container is a convenient way to deploy a home server solution within an isolated environment. By following the steps in this guide and ensuring that your LXC container is properly configured, you can create a powerful and customizable home server using CasaOS. Enjoy exploring the features and capabilities of CasaOS for your home automation and media server needs.