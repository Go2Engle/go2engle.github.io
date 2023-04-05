---
title: Generate and Copy SSH key to remote host from powershell
date: 2023-04-05
categories: [How-to, Powershell]
tags: [powershell,terminal]     # TAG names should always be lowercase
---

# Generating SSH keys in PowerShell
To generate SSH keys in PowerShell, follow these steps:

1. Open PowerShell by clicking the Start button and searching for PowerShell.

2. Type `ssh-keygen` and press Enter. This will start the process of generating your SSH keys.

3. You'll be prompted to enter a file name for your keys. The default file name is `id_rsa`, which is fine for most use cases. Press Enter to accept the default file name.

4. You'll be prompted to enter a passphrase for your keys. This is optional, but highly recommended for added security. If you don't want to use a passphrase, simply press Enter twice.

5. Your keys will be generated and saved to your user profile directory in the .ssh folder. By default, this directory is located at `$env:USERPROFILE\.ssh`. You should see two files: id_rsa (your private key) and id_rsa.pub (your public key).

# Copying SSH keys to a remote Linux host
Once you've generated your SSH keys, you'll need to copy them to the remote Linux host that you want to connect to. To do this, follow these steps:

1. Open PowerShell and type the following command, replacing <HOST_NAME> with the name or IP address of the remote Linux host:
    ```powershell
    type $env:USERPROFILE\.ssh\id_rsa.pub | ssh $env:UserName@<HOST_NAME> "mkdir .ssh && touch .ssh/authorized_keys && cat >> .ssh/authorized_keys"
    ```
2. Press Enter to run the command. You'll be prompted to enter the password for your user account on the remote Linux host.

3. Once you've entered your password, your public key will be copied to the remote host and added to the authorized_keys file in the .ssh directory. This will allow you to authenticate yourself using your private key when you connect to the remote host.

That's it! You've successfully generated SSH keys in PowerShell and copied them to a remote Linux host. Now you can use your private key to authenticate yourself when connecting to the remote host via SSH.