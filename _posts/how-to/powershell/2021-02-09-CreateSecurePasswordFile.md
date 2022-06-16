---
title: Create Secure Password File
date: 2021-02-09
categories: [How-to, Powershell]
tags: [powershell,scripts]     # TAG names should always be lowercase
---


## Method 1

```powershell
$MyCredentials=GET-CREDENTIAL -Credential "USERNAME" | EXPORT-CLIXML C:\Temp\SecureCredentials.xml
$MyCredentials=IMPORT-CLIXML C:\Temp\SecureCredentials.xml
```

## Method 2


To create the file run the below
```powershell
$credential = Get-Credential
$credential.Password | ConvertFrom-SecureString | Set-Content c:scriptsencrypted_password1.txt
```

To use the file
```powershell
$usename = "myemail"
$encrypted = Get-Content c:scriptsencrypted_password.txt | ConvertTo-SecureString
$credential = New-Object System.Management.Automation.PsCredential($usename, $encrypted)
```