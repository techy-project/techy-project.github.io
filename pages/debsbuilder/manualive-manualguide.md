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

Now, chroot it:
```
arch-chroot /mnt/archsys
```
## Hard disk environment
To update the initcpio, run this:
```
mkinitcpio -p linux
```
If you want to name your distro, open `/usr/lib/os-release` with your text-based text editor (nano, vim, etc.). /etc/os-release is a link to /usr/lib/os-release.

Then exit it:
```
exit
```
## Download the ISO files
To download the ISO files, use `bareimgf`. `bareimgf` stands for **Bare** **Im**a**g**e **F**iles.

For UEFI:
```
bareimgf --efi
```
For BIOS:
```
bareimgf --bios
```
