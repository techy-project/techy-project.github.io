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
To exit the iwd shell, type:
```
exit
```
## Mount your hard disk
To mount it, make sure:
- You have the latest Arch Linux.

Make the directory for mounting:
```
mkdir -p /mnt/archsys
```
Mount the hard disk on the directory:
```
mount /dev/sdax /mnt/archsys
```
- Replace sdax with your root partition. Enter `lsblk` to see the list of the disks and partitions.

Now, if you need to configure, then chroot it:
```
arch-chroot /mnt/archsys
```
