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
#### Chrooting
Before chrooting, please do these:
```
mount -t proc /proc /mnt/sys/proc
mount -t sysfs /sys /mnt/sys/sys
mount --rbind /dev /mnt/sys/dev
mount --rbind /run /mnt/sys/run
```
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
#### On Yequox live medium
To download the ISO files, use `bareimgf`. `bareimgf` stands for **Bare** **Im**a**g**e **F**etcher.

For UEFI:
```
bareimgf --efi
```
For BIOS:
```
bareimgf --bios
```
#### On other live medium
Yequox only has bareimgf. While on other live medium, use `wget`.

For UEFI:
```
wget https://archive.org/download/cdfiles/CDfiles-uefi.zip
```
For BIOS:
```
wget https://archive.org/download/cdfiles/CDfiles-bios.zip
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
##### GRUB files
###### Overwrite and copy
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

Copy your whole GRUB files:
```
cp /mnt/sys/boot/grub/ boot/grub -R
```
###### Remaking the EFI (UEFI only)
Oops! The EFI files are only used for systemd-boot and not for GRUB. They are unused.

Remove the unused EFI files:
```
rm EFI/BOOT/*
```
Remake with x86_64-efi:
```
grub-mkimage -o EFI/BOOT/bootx64.efi -c boot/grub/grub.cfg -p boot/grub -O x86_64-efi efi_gop efi_uga efinet all_video video video_bochs video_cirrus video_fb videoinfo serial terminfo terminal search search_fs_file search_fs_uuid search_label udf iso9660 ext2 fat exfat ntfs hfsplus part_gpt part_msdos msdospart lvm diskfilter parttool probe normal acpi ohci uhci ahci ehci cat ls lsefimmap lsefisystab lsmmap lspci lsacpi lssal linux
```
Remake with i386-efi:
```
grub-mkimage -o EFI/BOOT/bootia32.efi -c boot/grub/grub.cfg -p boot/grub -O i386-efi efi_gop efi_uga efinet all_video video video_bochs video_cirrus video_fb videoinfo serial terminfo terminal search search_fs_file search_fs_uuid search_label udf iso9660 ext2 fat exfat ntfs hfsplus part_gpt part_msdos msdospart lvm diskfilter parttool probe normal acpi ohci uhci ahci ehci cat ls lsefimmap lsefisystab lsmmap lspci lsacpi lssal linux
```
To see formats available, type:
```
ls /usr/lib/grub
```
##### Create and remove unused things
To remove unused things, use:
```
rm -rf arch/
rm boot/*.uuid
```
To create a new directory for SquashFS and most images, use:
```
mkdir live
```
###### Copying initramfs and vmlinuz
Copy these files to live/:
```
cp /mnt/sys/boot/initrd.img live/initrd.img
cp /mnt/sys/boot/vmlinuz live/vmlinuz
```
If those files are named differently, replace them.
##### Create a distribution version
You need a distribution version, to create it, use:
```
echo version > version
```
Replace the first "version" with your distribution version. For example:
```
echo 24.0 > version
```
###### Make a md5sum (optional)
To make the distribution version verified with md5sum, use:
```
md5sum version > version.md5sum
```
##### Make a SquashFS image
We need a SquashFS image. To make it, you need to run:
```
mksquashfs /mnt/sys /mnt/sys/filesystem.squashfs
```
Make sure you don't have unnecessary files and directories.
##### Copy ISO files
We need to copy ISO files to your root directory.

Run:
```
mkdir /mnt/sys/isofiles
cp ~/cdfiles/* /mnt/sys/isofiles -R
```
###### Reboot
We need to reboot to the hard disk to make a ISO.
To simply reboot:
```
reboot
```
### Make the ISO
