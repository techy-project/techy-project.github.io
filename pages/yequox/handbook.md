# The Yequox Handbook
The Yequox Handbook is the handbook that helps users to build their Linux distribution manually. It is included as a desktop shortcut on the Fedora-based Yequox live distribution.

Yequox BEF has steps before building the distro.

Yequox AFT has steps after building the distro.
## Yequox BEF (Part 1)
### Root
Enter the root user environment:
```
sudo su
```
### Connect to the Wi-Fi network
Before that, connect to your Wi-Fi network.
#### NetworkManager (recommended)
Click on the network icon on the bottom panel and search for your Wi-Fi network.
#### iwctl
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
### Mount your hard disk
To mount it, make sure:
- You have the latest distribution.

Make the directory for mounting:
```
mkdir -p /mnt/sys
```
Mount the hard disk on the directory:
```
mount /dev/sdax /mnt/sys
```
- Replace sdax with your root partition. Enter `lsblk` to see the list of the disks and partitions.

Now, chroot it:
```
chroot /mnt/sys /bin/bash
```
### Hard disk environment
To update the initramfs, run this:
```
update-initramfs -u
```
If you have dracut, run:
```
dracut
```

Then exit it:
```
exit
```
### Download the ISO files
To download the ISO files, use `bareimgf`. `bareimgf` stands for **Bare** **Im**a**g**e **F**etcher.

For UEFI:
```
bareimgf --efi
```
For BIOS:
```
bareimgf --bios
```
## Yequox AFT (Part 2)
### Extracting & modifying the ISO files
#### Extracting
To make the directory before extracting, use:
```
mkdir -p cdfiles
```
To extract the ISO files, use:
```
unzip CDfiles-* -d cdfiles
```
#### Modifying
Before modifying, change directory:
```
cd cdfiles
```
Overwrite `boot/grub/loopback.cfg` with this:
```
menuentry "Live system (x86_64)" --class gnu-linux --class gnu --class os --id 'live' {
	set gfxpayload=keep
	linux	/live/vmlinuz quiet splash ---
	initrd	/live/initrd.img
}
menuentry "Live system (x86_64, safe graphics)" --class gnu-linux --class gnu --class os --id 'livesafe' {
	set gfxpayload=keep
	linux	/live/vmlinuz nomodeset quiet splash ---
	initrd	/live/initrd.img
}
```
You can change the entry names, ID, timeout time, and add more entries.

Copy your GRUB configuration:
```
cp /mnt/sys/boot/grub/grub.cfg boot/grub
```
If your configuration is located at the other directory, it is still recommended to generate your GRUB configuration at `/boot/grub`.
