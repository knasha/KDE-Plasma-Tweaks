# KDE-Plasma-Tweaks
This document covers some tweaks I have to make usually when setting up a new KDE Plasma environment. Tweaks in this document may only be relevant to users running similar software and hardware setups.

## Epomaker Keyboard Tweaks - Enable Function Keys
This tweak disables "Mac" mode on Epomaker keyboards and forces Windows mode, which enables the function keys. Otherwise, the function keys behave like multimedia keys, which is annoying.
```bash
echo "options hid_apple fnmode=2" | sudo tee /etc/modprobe.d/hid_apple.conf
echo 'install_items+=/etc/modprobe.d/hid_apple.conf' | sudo tee /etc/dracut.conf.d/hid_apple.conf
sudo dracut --force
sudo reboot
```

## Easy Effects - Loudness Equalization on Linux

This tweak enables loudness equalization on Linux which is inexplicably missing on most if not all distros I have tested.

- Download `LoudnessEqualizer.json` config file from: https://github.com/Digitalone1/EasyEffects-Presets
- Install and then launch `Easy Effects` (This creats config folders)
- Paste json file in `~/.config/easyeffects/output` folder
- In Easy Effects, click `Presets` on top left.
- Select the config, and press Load
- Click `Effects` at the bottom
- Select `Gate`
- Raise Input Gain slider to `20.0 dB`
- Click `Presets` and save changes
- Click `Preferences` by clicking the menu on top right
- Enable `Launch Service at System Startup`
- Close Easy Effects

## Docker and QEMU don't work well together

This tweak fixes NAT related issues with QEMU if Docker is also installed on the same machine.

```bash
sudo vim /etc/libvirt/network.conf
```

Find and uncomment (or add) this line:
```
firewall_backend = "iptables"
```

## Bluetooth Audio Stutter Fix

ERTM causes retransmission storms that starve A2DP. 

```bash
echo "options bluetooth disable_ertm=1" | sudo tee /etc/modprobe.d/bluetooth.conf
sudo reboot
```
## Bluetooth Headset not becoming default
Recent updates to plasma (6.7.0) has caused this bug where if a bluetooth audio device is connected, the volume knob on the keyboard no longer controls it. This is because the previous device is still set as default. The following config file fixes this.

```bash
mkdir -p ~/.config/wireplumber/wireplumber.conf.d
vim ~/.config/wireplumber/wireplumber.conf.d/90-autoswitch.conf
```
Place the following text in this config file
```
wireplumber.settings = {
  device.restore-routes = false
}
```
Disconnect and reconnect the bluetooth device to test.
