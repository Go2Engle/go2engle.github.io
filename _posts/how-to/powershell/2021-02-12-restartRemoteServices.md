---
title: Restart remote services
date: 2021-02-12
categories: [How-to, Powershell]
tags: [powershell,scripts]     # TAG names should always be lowercase
---


Simple script to loop through multiple servers and services and restart the services. Just replace server and service names and run.

```powershell
## define your servers in an array
$Servers = "Server1","Server2","Server3"
## define your services in an array
$Services = "Service1","Service1","Service1"

## Loop through server array
foreach($Server in $Servers){
    ## Loop through service array
    foreach($Service in $Services){
        Write-Host "Restarting service $Service on $Server" -ForegroundColor Green
        ## Restart the service on the remote server
        Invoke-Command -ComputerName $Server -ScriptBlock{
            Restart-Service -Name $using:Service
        }
    }
}
```