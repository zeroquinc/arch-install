# Things to do after an Arch install

## Dual monitors with different refresh rates on NVIDIA

In terminal:

`sudo nano /etc/environment/` 

Add the following lines:

```
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

## Enable emoji's

In terminal:

`sudo pacman -S noto-fonts-emoji`

To enable emoji's in notifications and windows:

`sudo pacman -S noto-color-emoji-fontconfig`
