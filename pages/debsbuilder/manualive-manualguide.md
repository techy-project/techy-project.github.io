# The manual guide to build a Arch-based distribution/system
This is the guide for building a Arch-based distro on a ManuaLive live distribution.
## Connect to the Wi-Fi network
To connect to the Wi-Fi network, use `iwctl`.
To enter, you must type:
```
iwctl
```
Now, you're on the iwd shell. To connect it, type:
```
station wlanx connect "<wi-fi-name>"
```
- Replace `<wi-fi-name>` with your actual Wi-Fi network name.
- Replace x (wlanx) with your number, for example, 0 (wlan0).

Type your network's password (or you don't have it).
To exit, type:
```
exit
```
