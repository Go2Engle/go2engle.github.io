---
title: Outlook new email
date: 2021-02-11
categories: [How-to, Powershell]
tags: [powershell,scripts]     # TAG names should always be lowercase
---


The below code allows you to open a new email message via outlook on your local PC.

```powershell
$ol = New-Object -comObject Outlook.Application
#Create the new email
$mail = $ol.CreateItem(0)
#Optional, set the subject
$mail.Subject = "<subject>"
#Optional, set the body
$mail.Body = "<body>"
#Get the new email object
$inspector = $mail.GetInspector
#Bring the message window to the front
$inspector.Activate()
```