# Quick Links

## Arch
- [Dual monitors with different refresh rates on NVIDIA](#dual-monitors-with-different-refresh-rates-on-nvidia)
- [Install Pamac](#install-pamac)
- [Enable Emoji](#enable-emoji)

## Ubuntu
- [2 Different SSH profiles for GitHub on Ubuntu](#2-different-ssh-profiles-for-github-on-ubuntu)
- [Aliasses to make custom commands for terminal](#aliasses-to-make-custom-commands-for-terminal)

# Arch

## Dual monitors with different refresh rates on NVIDIA

In terminal:

`sudo nano /etc/environment/` 

Add the following lines:

```zsh
KWIN_X11_REFRESH_RATE=144000 #change value to your highest refresh rate
KWIN_X11_NO_SYNC_TO_VBLANK=1
KWIN_X11_FORCE_SOFTWARE_VSYNC=1
CLUTTER_DEFAULT_FPS=144 #change value to your highest refresh rate
__GL_SYNC_DISPLAY_DEVICE=DP-2 #change value to your highest refresh rate monitor name
__GL_SYNC_TO_VBLANK=0
```

In terminal:

`sudo nvidia-settings`

- Enable `Force Composition Pipeline` for both monitors.
- Uncheck `Sync to VBlank` and `Allow Flipping`.
- Under `X Server XVideo Settings` set the synced display to your highest refresh rate.
- Save to X Configuration File.

## Install Pamac

In terminal:

`yay -S pamac-aur`

- Open Pamac and go to Preferences -> Third Party
- Make sure these settings are checked.

<img src="https://user-images.githubusercontent.com/39315068/194762868-aea3a60b-5047-463c-a3a2-f6679b4773a6.png" width=50% height=50%>

## Enable emoji

In terminal:

`sudo pacman -S noto-fonts-emoji`

To enable emoji's in notifications and windows:

`sudo pacman -S noto-color-emoji-fontconfig`

# Ubuntu

## 2 Different SSH profiles for GitHub on Ubuntu

**Step 1: ssh keys**

Create any keypairs you'll need. In this example I've named me default/original 'id_rsa' (which is the default) and my new one 'id_rsa-work':

```ssh-keygen -t rsa -C "stefano@work.com"```

**Step 2: ssh config**

Set up multiple ssh profiles by creating/modifying ~/.ssh/config. Note the slightly differing 'Host' values:
```
# Default GitHub
Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa

# Work GitHub
Host work.github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_work
```

**Step 3: ssh-add**

You may or may not have to do this. To check, list identity fingerprints by running:
```
$ ssh-add -l
2048 1f:1a:b8:69:cd:e3:ee:68:e1:c4:da:d8:96:7c:d0:6f desiler (RSA)
2048 6d:65:b9:3b:ff:9c:5a:54:1c:2f:6a:f7:44:03:84:3f zeroquinc (RSA)
```
If your entries aren't there then run:
```
ssh-add ~/.ssh/id_rsa_work
```

**Step 4: test**

To test you've done this all correctly, I suggest the following quick check:
```
$ ssh -T git@github.com
Hi desiler! You've successfully authenticated, but GitHub does not provide shell access.

$ ssh -T git@work.github.com
Hi zeroquinc! You've successfully authenticated, but GitHub does not provide shell access.
```
Note that you'll have to change the hostname (github / work.github) depending on what key/identity you'd like to use. But now you should be good to go! :)

## Aliasses to make custom commands for terminal

If you want to create a simple command to tail the log file, you can create an alias in your shell.

You can add the following line as example to your ~/.bash_aliases file:

```alias skywalkerlogs="tail -f /opt/scripts/Code/ServerBot_v2/logs/serverbot.log"```

Then, source your ~/.bash_aliases file to apply the changes:

```source ~/.bash_aliases```

Now, you can use the ```tailserverbot``` command to tail the log file.

