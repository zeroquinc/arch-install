# Things to do after an Arch install

1. `sudo nano /etc/environment/` and add the following lines;

```
KWIN_X11_REFRESH_RATE=144000
KWIN_X11_NO_SYNC_TO_VBLANK=1
KWIN_X11_FORCE_SOFTWARE_VSYNC=1
CLUTTER_DEFAULT_FPS=144
__GL_SYNC_DISPLAY_DEVICE=DP-2
__GL_SYNC_TO_VBLANK=0
```

2. `sudo nvidia-settings`

Enable `Force Composition Pipeline` for both monitors.
Uncheck `Sync to VBlank` and `Allow Flipping`.

Under `X Server XVideo Settings` set the synced display to your highest refresh rate.

Save to X Configuration File.
