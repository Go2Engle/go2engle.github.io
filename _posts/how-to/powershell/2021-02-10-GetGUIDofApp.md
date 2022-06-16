---
title: Get GUID of applications installed on a computer
date: 2021-02-10
categories: [How-to, Powershell]
tags: [powershell,scripts]     # TAG names should always be lowercase
---


Open powershell and run the bellow command.

```powershell
get-wmiobject Win32_Product | sort-object -property Name | Format-Table IdentifyingNumber, Name, LocalPackage -AutoSize
```