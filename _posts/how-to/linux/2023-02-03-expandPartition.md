---
title: Extend the disk size of a Ubuntu VM 
date: 2023-02-03
categories: [How-to, Linux]
tags: [ubuntu,vm,customize]     # TAG names should always be lowercase
---

## Introduction

Running out of space on your VM and need to increase the storage of your main partition? All you need to do is add more disk capacity in your hypervisor and extend your partition.

## Dependencies

Parted must be installed to follow the below steps. If you do not have parted you can install with:
```shell
sudo apt-get install parted
```

## Steps
1. Extend your disk to your desired size in your hypervisor.
2. SSH into the VM.
3. Run `df -h` to check your current space for refrence.
4. Run `sudo parted` to enter into parted.
5. Type `print` and hit Enter.
6. If asked to fix type `fix` and hit Enter.
7. You will see your partitions. In most cases if you have the default partition layout we will be working with partition 2. Type `resizepart 2` and hit Enter.
8. When asked for End value look for the `Disk /dev/sda` value from the print command above and enter in format of `80GB` for example.
9. Type `q` and hit enter.
10. Run `sudo resize2fs /dev/sda2`.
11. Run `df -h` to confirm partition expanded.