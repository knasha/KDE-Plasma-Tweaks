# KDE-Plasma-Tweaks
This document covers some tweaks I have to make usually when setting up a new KDE Plasma environment. Tweaks in this document may only be relevant to users running similar softward and hardware setups.

## Epomaker Keyboard Tweaks - Enable Function Keys
This tweak disables "Mac" mode on Epomaker keyboards and forces Windows mode, which enables the function keys. Otherwise, the function keys behave like multimedia keys, which is annoying.
```bash
echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode
```
