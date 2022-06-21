---
title: OhMyZSH Shell setup    
date: 2022-06-20
categories: [How-to, Linux]
tags: [shell,ubuntu,terminal,customize]     # TAG names should always be lowercase
---

Below are all the steps to configure your terminal to look like the screenshot

![Shell](/assets/img/how-to/linux/shellSetup/shell.png)

1. Install ZSH and set as default shell.
```shell
sudo apt install zsh
```
2. Install OhMyZSH.
```shell
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
3. Download and install the below fonts. Once installed set your terminal font to `MesloLGS NF`. [Source](https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k)
- [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
- [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
- [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
- [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)
4. Install Powerlevel10k theme.
```shell
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
5. Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc.`
6. Restart ZSH.
```shell
exec zsh
```
7. Type `p10k configure` if the configuration wizard doesn't start automatically.
8. Install zsh-autosuggestions. [Source](https://github.com/zsh-users/zsh-autosuggestions)
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
9. Add the plugin to the list of plugins for Oh My Zsh to load (inside `~/.zshrc`):
```shell
plugins=( 
    # other plugins...
    zsh-autosuggestions
)
```
10. Create a .zsh file to add customizations to for autosuggestions.    
```shell
nano ~/.oh-my-zsh/custom/zsh-autosuggestions.zsh
```
11. Add the below in the created file
```shell
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#87ff87"
ZSH_AUTOSUGGEST_STRATEGY=(history completion)
```
12. Restart your terminal.