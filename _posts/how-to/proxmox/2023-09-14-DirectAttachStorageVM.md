---
title: Directly Attaching Disks to VMs in Proxmox
date: 2023-09-14
categories: [How-to, Proxmox]
tags: [proxmox,howto,storage]     # TAG names should always be lowercase
---

Proxmox Virtual Environment (PVE) is a versatile virtualization platform that provides a wide range of features for managing virtual machines (VMs). One powerful capability is the ability to directly attach physical disks to VMs. This can be particularly useful when you want to provide dedicated storage to a VM, pass through specialized hardware, or create high-performance storage solutions. In this guide, we'll walk you through the process of directly attaching disks to VMs in Proxmox.

## Prerequisites

Before you begin, ensure that you have:

1. A Proxmox Virtual Environment (PVE) server up and running.
2. A physical disk that you want to attach to a VM. Make a note of its serial number or identifier.

## Step 1: Update Package Repositories

To ensure your system is up to date, log in to your Proxmox server and run the following commands:

```shell
apt update
```

## Step 2: Install 'lshw' for Hardware Information

To gather information about the available disks and their identifiers, you can use the `lshw` tool. If it's not already installed, you can install it by running:

```shell
apt install lshw
```

## Step 3: Identify the Disk to Attach

Now, let's use `lshw` to identify the disk that you want to attach to your VM. Run the following command to list information about disks and storage devices:

```shell
lshw -class disk -class storage
```

This command will provide detailed information about the disks on your system, including their serial numbers or identifiers. Make note of the serial number or identifier of the disk you want to attach.

## Step 4: Create a Symlink to the Disk

Next, you need to create a symlink to the disk using its serial number or identifier. Replace `<serial of disk>` with the actual serial number or identifier of your disk:

```shell
ls -l /dev/disk/by-id | grep <serial of disk>
```

This command will display the symlink associated with your disk. Make a note of the symlink, as you will use it in the next step.

## Step 5: Attach the Disk to the VM

Now that you have the symlink to your disk, you can attach it to the VM. Use the following command, replacing `<vm id>` with the actual ID or name of your VM, and `<ata-**>` with the symlink from the previous command:

```shell
qm set <vm id> -scsi2 /dev/disk/by-id/<ata-**>
```

This command tells Proxmox to attach the specified disk to the VM as a SCSI device. You can use different SCSI controllers (e.g., `-scsi0`, `-scsi1`, `-scsi2`, etc.) for attaching multiple disks to the same VM.

## Conclusion

Directly attaching disks to VMs in Proxmox provides flexibility and performance advantages, allowing you to tailor your virtualized environments to specific needs. By following these steps, you can seamlessly integrate physical disks into your virtual machines, expanding storage, and maximizing the utility of your Proxmox environment.

Keep in mind that attaching disks directly to VMs requires careful consideration of hardware compatibility, performance requirements, and data management. Always ensure that you have adequate backups and follow best practices when dealing with storage in virtualized environments.