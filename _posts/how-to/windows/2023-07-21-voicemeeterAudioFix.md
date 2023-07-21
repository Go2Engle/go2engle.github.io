---
title: Fixing Microphone Quality with Voicemeeter and Discord using PowerShell
date: 2023-07-21
categories: [How-to, Windows, Powershell]
tags: [windows,powershell,audio,discord,voicemeeter,scripts,automation]     # TAG names should always be lowercase
---

## Introduction

For users who run Voicemeeter and Discord simultaneously, experiencing microphone quality issues like choppiness and distortion can be quite common. These problems can negatively impact communication, making it essential to find a solution. In this article, we'll explore a PowerShell script that can potentially improve microphone quality by adjusting the priority of the `audiodg.exe` process when using Voicemeeter and Discord together.

## Understanding the Issue

The microphone quality issues stem from how Windows handles audio processing when multiple applications, such as Voicemeeter and Discord, compete for system resources.

`audiodg.exe` is a Windows system process responsible for managing audio processing and effects. Running multiple audio applications concurrently can lead to audio glitches and choppy microphone quality as they contend for resources. By elevating the priority of `audiodg.exe` to a higher level, we can potentially allocate more resources to audio processing, which may result in improved microphone sound.

## The Solution - PowerShell Script

To streamline the process of setting the priority of `audiodg.exe` to high, we'll use a PowerShell script. This script will run automatically at startup, ensuring that the priority adjustment occurs each time the system boots.

### Creating the PowerShell Script

Below is the PowerShell script that needs to be created:

```powershell
# Get the audiodg.exe process
$audioProcess = Get-Process -Name "audiodg" -ErrorAction SilentlyContinue

if ($audioProcess) {
    try {
        # Set the process priority to High
        $audioProcess.PriorityClass = [System.Diagnostics.ProcessPriorityClass]::High
        Write-Host "Priority of audiodg.exe set to High."
    } catch {
        Write-Host "Failed to set priority for audiodg.exe. Error: $_" -ForegroundColor Red
    }
} else {
    Write-Host "audiodg.exe process not found." -ForegroundColor Red
}
```

### Configuring the Scheduled Task

1. Open Task Scheduler: Press `Win + R`, type `taskschd.msc`, and press Enter.

2. In Task Scheduler, click on "Create Basic Task" in the right-hand Actions pane.

3. Give your task a name and description, then click "Next."

4. Choose "When the computer starts" and click "Next."

5. Select "Start a program" and click "Next."

6. Browse and select the PowerShell executable (`powershell.exe`). The default location is usually `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

7. In the "Add arguments (optional)" field, enter the full path to your PowerShell script. For example, if your script is in `C:\Scripts\set_audiodg_priority.ps1`, you would enter:
   ```
   -ExecutionPolicy Bypass -File "C:\Scripts\set_audiodg_priority.ps1"
   ```
   The `-ExecutionPolicy Bypass` parameter is added to bypass the execution policy and allow the script to run.

8. Click "Next" and then "Finish" to create the task.

## Conclusion

By utilizing the steps outlined in this article, you can set the priority of the `audiodg.exe` process to high, potentially enhancing microphone quality when using Voicemeeter and Discord together. However, it's essential to be cautious when modifying process priorities, as it can have consequences on system performance. Always test the script before automating it at startup and ensure that you have a backup of your system.

Remember that audio quality can be influenced by various factors, including hardware, drivers, and network settings. If the microphone quality issues persist, consider exploring other troubleshooting options or seeking assistance from relevant communities and forums.

Happy communicating with improved microphone quality!