# The Yequox Handbook
The Yequox Handbook is the handbook that helps users to build their Linux distribution manually. It is included as a desktop shortcut on the Ubuntu-based Yequox live distribution.


Yequox B.E.S. (Before Environment Setup) has steps before building the distro. (Enter root, connecting, mounting, chrooting, downloading the base ISO files.)

Yequox A.E.S. (After Environment Setup) has steps after building the distro. (Extracting & modifying the ISO files.)
## Yequox B.E.S. (Part 1)
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
##### bareimgf
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
##### wget
Yequox only has bareimgf. While on other live medium, use `wget`.

For UEFI:
```
wget https://archive.org/download/cdfiles/CDfiles-uefi.zip
```
For BIOS:
```
wget https://archive.org/download/cdfiles/CDfiles-bios.zip
```
##### curl
While the other distribution don't use wget, you can use `curl`.

For UEFI:
```
curl https://archive.org/download/cdfiles/CDfiles-uefi.zip
```
For BIOS:
```
curl https://archive.org/download/cdfiles/CDfiles-bios.zip
```
## Yequox A.E.S. (Part 2)
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
Fedora uses a different name like /boot/grub2, so, you need to replace them.
For Fedora systems:
```
cp /mnt/sys/boot/grub2 boot/grub -R
```
###### Remaking the EFI (UEFI only)
Oops! The EFI files are only used for systemd-boot and not for GRUB. They are unused.

Remove the unused EFI files:
```
rm EFI/BOOT/*
```
Remake with x86_64-efi:
```
grub-mkimage \
	-o EFI/BOOT/bootx64.efi \
	-c boot/grub/grub.cfg \
	-p boot/grub \
	-O x86_64-efi \
	efi_gop efi_uga efinet \
	all_video video video_bochs video_cirrus video_fb videoinfo \
	serial terminfo terminal \
	search search_fs_file search_fs_uuid search_label \
	udf iso9660 ext2 fat exfat ntfs hfsplus \
	part_gpt part_msdos msdospart lvm diskfilter parttool probe \
	normal acpi ohci uhci ahci ehci cat \
	ls lsefimmap lsefisystab lsmmap lspci lsacpi lssal \
	linux
```
Remake with i386-efi:
```
grub-mkimage \
	-o EFI/BOOT/bootia32.efi \
	-c boot/grub/grub.cfg \
	-p boot/grub \
	-O i386-efi \
	efi_gop efi_uga efinet \
	all_video video video_bochs video_cirrus video_fb videoinfo \
	serial terminfo terminal \
	search search_fs_file search_fs_uuid search_label \
	udf iso9660 ext2 fat exfat ntfs hfsplus \
	part_gpt part_msdos msdospart lvm diskfilter parttool probe \
	normal acpi ohci uhci ahci ehci cat \
	ls lsefimmap lsefisystab lsmmap lspci lsacpi lssal \
	linux
```
To see formats available, type:
```
ls /usr/lib/grub
```
##### Create and remove unused things
Oh no! There are unused things! So we originally used to be ManuaLive and based on Arch, but we switched to Ubuntu and chose Yequox.
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
###### Make the name (optional)
To make a name for your distro, try thinking about your name of your distribution.

To make it:
```
echo name > name.distro
```
For our name of the distribution "Yequox":
```
echo Yequox > name.distro
```
If your distribution name has spaces, try:
```
echo "name of the distribution" > name.distro
```
For example:
```
echo "Yequox Linux" > name.distro
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
##### Add more files
If you want to add more files, here:

###### GRUB formats
If you want to add more GRUB formats, here are the formats:
i386-pc and i386-efi if you want to make it bootable for BIOS and bootable for x86 UEFI.
###### i386 GRUB formats
To copy i386-efi, run:
```
cp /usr/lib/grub/i386-efi boot/grub -R
```
To copy i386-pc, run:
```
cp /usr/lib/grub/i386-pc boot/grub -R
```
Remove the previously generated GRUB config file:
```
rm boot/grub/grub.cfg
```
Regenerate it:
```
grub-mkconfig -o boot/grub/grub.cfg
```
###### Make more (optional)
To make more files:


To make a file with random numbers:
```
touch numb
echo $RANDOM > numb
```
You can make more files.

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
We are here now! So, act as a root user:
```
sudo su
```
Move the SquashFS:
```
mv /filesystem.squashfs /isofiles/live
```
And make the ISO:
```
genisoimage -r -V "ISO-LABEL" -cache-inodes -J -l \
  -b /isofiles/boot/syslinux/isolinux.bin -no-emul-boot \
  -boot-load-size 4 -boot-info-table -o iso-name.iso /isofiles
```
- Replace "ISO-LABEL" with your label. As shown here, the written USB should be the name of "Yequox Linux" as an example.
- Replace iso-name.iso with your ISO name.

If you don't have `genisoimage`, use these to install it:

Debian/Ubuntu systems:
```
apt install genisoimage
```
Fedora/Red Hat systems:
```
dnf install genisoimage
```
Arch systems:
```
pacman -S cdrkit
```
openSUSE systems:
```
zypper install genisoimage
```
### Testing the ISO
If you wanna test it on a VM, here:
#### Text-based
##### qemu-system-x86_64
To test it on QEMU, run:
```
qemu-system-x86_64 -boot d -cdrom iso-name.iso -m 1024
```
Replace iso-name.iso with your actual ISO.
#### Graphical
##### Virtual Machine Manager
Virtual Machine Manager is using QEMU. So, if you wanna test here, add your virtual machine here.
##### Others
Do the same thing as Virtual Machine Manager.
### Done!
Now your ISO is done and ready to go!
