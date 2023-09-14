---
title: Creating an Unprivileged LXC Container in Proxmox via the UI with KeyCTL Support
date: 2023-09-14
categories: [How-to, Proxmox]
tags: [docker,LXC,container,proxmox,howto]     # TAG names should always be lowercase
---

## Introduction

Proxmox Virtual Environment (PVE) is a powerful virtualization platform that allows you to run and manage various virtualization technologies, including Linux Containers (LXC). LXC containers are lightweight and efficient, making them an excellent choice for isolating applications and services. In this guide, we'll walk you through the process of creating an unprivileged LXC container in Proxmox using the user-friendly web interface. Additionally, we'll ensure that KeyCTL support is enabled, which is essential for certain container features.

## Prerequisites

Before you begin, make sure you have the following:

1. A Proxmox Virtual Environment (PVE) server set up and accessible.
2. Sufficient resources (CPU, RAM, and storage) available on your PVE server.
3. Administrative access to the Proxmox web interface.

## Step 1: Access the Proxmox Web Interface

Open a web browser and navigate to the Proxmox web interface. Typically, you can access it by entering the server's IP address or hostname in your browser's address bar, followed by the port number (default is 8006):

```
https://<your-server-ip>:8006/
```

Log in using your administrative credentials.

## Step 2: Create a New Unprivileged LXC Container

1. In the Proxmox web interface, click on "Create CT" on the left sidebar.

2. Fill in the necessary information to configure your LXC container:
   - **VM ID:** Enter a unique numeric identifier for your container.
   - **Hostname:** Choose a hostname for your container.
   - **Root Password:** Set a secure root password for the container.
   - **Unprivileged:** Ensure that the "Unprivileged" option is checked. This is essential for creating unprivileged containers.
   - **ISO Image:** Select an ISO image to install the container's operating system. You can upload an ISO to the server if it's not already available.

3. Click on the "Next" button to proceed.

4. Configure the container's resources:
   - Adjust CPU and memory as needed.
   - Allocate disk space by specifying the "Disk size (GB)."

5. Click "Next" to proceed.

6. Customize additional options and settings for your container as desired, such as network settings, DNS, and more.

7. Review your settings, and when you're ready, click "Finish" to create the container.

## Step 3: Enable KeyCTL Support

Before you start the LXC container, we need to enable KeyCTL support to ensure proper functionality of certain container features. Here's how to do it:

1. In the Proxmox web interface, click on "Datacenter" in the left sidebar.

2. Select your Proxmox node from the list on the right.

3. Go to the "Options" tab.

4. Under the "Features" section, find the "KeyCTL" option and ensure it's checked.

5. Click on "OK" to save the changes.

## Step 4: Start the Unprivileged LXC Container

Now that KeyCTL support is enabled, you can start your unprivileged LXC container:

1. In the Proxmox web interface, navigate to the "Container" section on the left sidebar.

2. Select the container you created in Step 2.

3. Click on the "Start" button at the top.

4. The container will start, and you can access its console or connect via SSH to begin configuring and using your unprivileged LXC container.

## Conclusion

Creating an unprivileged LXC container in Proxmox via the web interface is a straightforward process that offers many benefits in terms of resource isolation and security. Enabling KeyCTL support ensures that your container functions correctly, enabling advanced features as needed. With your container up and running, you're ready to deploy and manage applications within it, taking full advantage of containerization technology.