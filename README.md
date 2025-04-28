# KDE-Plasma-Tweaks
This document covers some tweaks I have to make usually when setting up a new KDE Plasma environment. Tweaks in this document may only be relevant to users running similar softward and hardware setups.

## Epomaker Keyboard Tweaks - Enable Function Keys
This tweak disables "Mac" mode on Epomaker keyboards and forces Windows mode, which enables the function keys. Otherwise, the function keys behave like multimedia keys, which is annoying.
```bash
echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode
```

## Easy Effects - Loudness Equalization on Linux

This tweak enables loudness equalization on Linux which is inexplicably missing on most if not all distros I have tested.

- Download `LoudnessEqualizer.json` config file from: https://github.com/Digitalone1/EasyEffects-Presets
- Launch Easy Effects (This creats config folders)
- Paste json file in `~/.config/easyeffects/output` folder
- In Easy Effects, click `Presets` on top left.
- Select the config, and press Load
- Click `Effects` at the bottom
- Select `Gate`
- Raise Input Gain slider to `20.0 dB`
- Click `Presets` and save changes
- Click `Preferences` by clicking the menu on top right
- Enable `Launch Service at System Startup`
