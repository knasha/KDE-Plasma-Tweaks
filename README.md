# KDE-Plasma-Tweaks
This document covers some tweaks I have to make usually when setting up a new KDE Plasma environment. Tweaks in this document may only be relevant to users running similar softward and hardware setups.

## Epomaker Keyboard Tweaks - Enable Function Keys
```bash
echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode
```
