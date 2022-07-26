---
title: Setting up Powershell profile in Windows Terminal
date: 2022-07-25
categories: [How-to, Powershell]
tags: [powershell,customization,terminal]     # TAG names should always be lowercase
---

The below steps will walk you through setting up your windows terminal with the latest powershell, oh-my-posh, and psreadline.

1. Install the latest version of powershell from [Microsoft](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.2)
2. Set your windows terminal default powershell to the latest that was just installed.
3. Use winget to install oh-my-posh.
    ```powershell
    winget install JanDeDobbeleer.OhMyPosh -s winget
    ```
4. Install fonts using oh-my-posh.
    ```powershell
    oh-my-posh font install
    ```
5. After fonts are installed change your windows terminal font defaults to `MesloLGM NF`. This will allow the themes to render correctly in your terminal.
6. Install PSReadLine powershell module using an elevated powershell session.
    ```powershell
    Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
    ```
7. Modify your powershell profile.
    ```powershell
    nodepad $PROFILE
    ```
    
    > If your prfoile does not exist create it with the below.
    ```powershell
    New-Item -Path $PROFILE -Type File -Force
    ```
    {: .prompt-info }

    ```powershell
    $ohmyposhTheme = "spaceship"
    oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\$ohmyposhTheme.omp.json" | Invoke-Expression
    Import-Module PSReadLine
    Set-PSReadLineOption -PredictionSource HistoryAndPlugin
    Set-PSReadLineOption -PredictionViewStyle ListView
    Set-PSReadLineOption -EditMode Windows
    ```

> You can view oh-my-posh themes by running `Get-PoshThemes`.
> After you find a theme you like change `$ohmyposhTheme = "spaceship"` in your profile and save.
{: .prompt-tip }