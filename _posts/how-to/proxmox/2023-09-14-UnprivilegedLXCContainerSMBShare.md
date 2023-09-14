---
title: Mounting SMB Shares Inside an Unprivileged Proxmox LXC Container for Docker
date: 2023-09-14
categories: [How-to, Proxmox]
tags: [docker,LXC,container,proxmox,howto,smb,shares]     # TAG names should always be lowercase
---

## Introduction

In the world of containerization, Proxmox is a powerful virtualization platform that allows you to create and manage Linux containers (LXC) efficiently. These containers can run various applications, including Docker containers. In this guide, we'll walk you through the process of mounting SMB shares inside an unprivileged Proxmox LXC container for use with Docker. This can be especially useful when you need to access remote storage resources securely within your containerized applications.

## Prerequisites

Before we dive into the steps, ensure that you have already set up an unprivileged LXC container on your Proxmox Virtual Environment (PVE). If you haven't done this yet, you can follow our previous guide on [setting up an unprivileged LXC container](https://go2engle.com/posts/UnprivilegedLXCContainerDocker/). Once your LXC container is up and running, you can proceed with the following steps.

## Step 1: Stop the LXC Container

To safely configure SMB share access, stop your LXC container. You can do this using the Proxmox web interface or via the command line with the following command:

```shell
pct stop <container-id>
```

Replace `<container-id>` with the actual ID or name of your LXC container.

## Step 2: Create Folders for Mounting SMB Share

On your Proxmox host, create a directory where you will mount the SMB share. For this example, let's create a folder named "media" under the "/mnt" directory:

```shell
mkdir /mnt/media
```

You can choose a different directory path based on your requirements.

## Step 3: Edit the fstab File

Now, you need to edit the "/etc/fstab" file to configure the automatic mounting of the SMB share. Use your preferred text editor to open the file; for example, you can use Nano:

```shell
nano /etc/fstab
```

Inside the "fstab" file, add the following line, making sure to replace placeholders with your specific information:

```shell
//HOST/SHARE   /mnt/media   cifs   x-systemd.automount,username=USERNAME,password=PASSWORD,uid=101000,gid=101000   0   0
```

- Replace "HOST" with the hostname or IP address of the SMB server.
- Replace "SHARE" with the name of the shared folder or resource you want to access.
- Replace "USERNAME" and "PASSWORD" with the credentials required to access the SMB share.

Your modified "fstab" file should look something like this:

```shell
//192.168.1.100/shared_folder   /mnt/media   cifs   x-systemd.automount,username=myuser,password=mypassword,uid=101000,gid=101000   0   0
```

Save the changes and exit your text editor.

## Step 4: Reload systemd and Mount the SMB Share

After editing the fstab file, you need to reload systemd and mount the SMB share. Run the following commands:

```shell
systemctl daemon-reload
mount -a
```

## Step 5: Start the LXC Container

With the SMB share configured and mounted, you can now start your LXC container:

```shell
pct start <container-id>
```

Replace "<container-id>" with the actual ID or name of your LXC container.

## Conclusion

You've successfully configured your Proxmox LXC container to mount an SMB share, allowing your containerized applications to access remote storage resources securely. This setup can be particularly beneficial for applications like Docker containers that require access to external data or media files.