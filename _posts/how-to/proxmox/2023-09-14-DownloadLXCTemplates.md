---
title: How to Download and Add New LXC Container Templates in Proxmox GUI
date: 2023-09-14
categories: [How-to, Proxmox]
tags: [proxmox,howto,LXC,templates]     # TAG names should always be lowercase
---

Proxmox VE is an open-source server management platform for enterprise virtualization that tightly integrates the KVM hypervisor and Linux Containers (LXC), software-defined storage and networking functionality, on a single platform. In this tutorial, we will discuss how to download and add new LXC container templates in Proxmox GUI.

## Step 1: Access the Proxmox GUI

To access the Proxmox GUI, open your web browser and enter the IP address of your Proxmox server followed by port 8006. For example, `https://192.168.1.100:8006/`.

## Step 2: Access the Container Templates

Once you have accessed the Proxmox GUI, click on the "Datacenter" node in the left-hand navigation pane. Then, click on the "Storage" tab and select the storage where you want to download the LXC container template. Next, click on the "CT Templates" option and then click the "Templates" button.

## Step 3: Download the LXC Container Template

In the "Templates" window, you will see a list of available LXC container templates. You can either download a template by clicking the "Download" button or upload an already downloaded template by clicking the "Upload" button. You can also choose the "Download from URL" button to download the template from a specific URL.

## Step 4: Add the LXC Container Template

After downloading the LXC container template, you can add it to the Proxmox server by clicking on the "Create CT" button in the left-hand navigation pane. In the "Create CT" window, select the downloaded LXC container template from the "Template" drop-down list. Then, enter the required information for the new container, such as the hostname, IP address, and password.

## Conclusion

In this tutorial, we have discussed how to download and add new LXC container templates in Proxmox GUI. With this knowledge, you can easily download and add new LXC container templates to your Proxmox server and create new containers based on those templates.