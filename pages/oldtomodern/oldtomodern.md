# OldTOModern
**OldTOModern** (abbreviated as **OTM**) is a pack for Linux desktops that replaces old themes with modern themes. Development began on July 27, 2024, then fully released on July 31, 2024.
# OTM Pack
The **OTM Pack** is a larger pack for **OldTOModern**, it is 600+ MB, it is a .zip, and it is recommended to use the **OTM Pack**. The **OTM Pack** has various packs including CerSer, Eyecon, BWsP and more, it also includes the pack types like modern and old.
## Modern
The modern packs includes CerSer, Eyecon, BWsP, Splesh and OFK.
### CerSer
**CerSer** is a modern cursor theme pack, included in the **OTM Pack**.
### Eyecon
**Eyecon** (pronounced icon) is a modern icon theme pack, included in the **OTM Pack**.
### BWsP
**BWsP** (or **B**ackground **W**allpaper**s** **P**ack) is a modern wallpaper pack, included in the **OTM Pack**.
### Splesh
**Splesh** (pronounced splash) is a modern splash screen pack for KDE Plasma 5 and 6, included in the **OTM Pack**.
### OFK
**OFK** (or **O**ldTOModern **F**or **K**DE) is an modern OTM pack for KDE 3 and 4, included in the **OTM Pack**.
## Old
The old packs includes WBCS, EyeIIP, Splesh4, Spl3sh.
### WBCS
**WBCS** (or **W**hile **B**ack **C**er**S**er) is an old cursor theme pack, included in the **OTM Pack**.
### EyeIIP
**EyeIIP** (or I Integration Icon Pack) is an old icon theme pack, included in the **OTM Pack**.
### Splesh4
**Splesh4** is an old splash screen pack for KDE 4, included in the **OTM Pack**.
### Spl3sh
**Spl3sh** (pronounced sp-l-three-sh) is an old splash screen pack for KDE 3, included in the **OTM Pack**.
# Downloads
The OTM Pack is a larger .zip, and it is recommended. [Download OTM Pack.](https://archive.org/download/otm-files/otm_pack-v24.zip)

Or, you just wanna only get the OFK pack, and it is 200+ MB. [Download OFK.](https://archive.org/download/otm-files/otm_for_kde-v24.zip)
# How to turn it into the ISO image?
Well, it is pretty easy when you are trying to use the OTM Pack on your Linux VM, instead of using shared folders.

Change your directory to this:

```
cd ~/Downloads
```

Extract the OTM Pack using Ark, Archive Manager or etc.

Make the ISO:

```
genisoimage -o otm_pack.iso otm_pack-v*/
```

If you don't have `genisoimage`, install **genisoimage** on your distro, or **cdrkit** on your Arch or Arch-based distro.

Verify the ISO:

```
ls | grep otm_pack.iso
```

You are complete! You can now import the OTM Pack on your VM.
