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

## Linux

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

## Windows

On Windows, you can use AnyBurn to create ISO images from files/folders.

Download the AnyBurn installer:

![image](https://github.com/user-attachments/assets/1ee58424-f36e-4644-8892-f0ede7cd9be7)

AnyBurn has 2 editions like Free and Pro. The Free edition is free for personal use. The Pro edition is free for trial.

Once you installed it, open AnyBurn:

![image](https://github.com/user-attachments/assets/d1acbc16-c5f0-4059-b76e-17e45813dea6)

This shows up:

![image](https://github.com/user-attachments/assets/f7b07c06-be36-43a9-ad1e-a63aa2487fda)

Click "Create image file from files/folders".

![image](https://github.com/user-attachments/assets/30b7f119-d891-4bdb-afb1-3b3c36021e60)

Make sure you downloaded the OTM Pack. Scroll up for downloads.

To extract the .zip file, use 7-Zip if you prefer FOSS software, or WinRAR if you prefer proprietary software.

![image](https://github.com/user-attachments/assets/0fddcecc-9eab-4bbe-95cd-ece6586663cd)

After clicking "Create image file from foles/folders" this will show up.

![image](https://github.com/user-attachments/assets/ddb4accc-cf8b-4cf8-8861-7e5827419d3b)

Change the ISO label to "OTM Pack". (optional)

![image](https://github.com/user-attachments/assets/17ea0e81-79e9-4013-8bcd-541ca1c34142)

Click the add button to add files/folders to your ISO image.

![image](https://github.com/user-attachments/assets/9ece8205-45cf-45ad-bd00-8199fcc979e3)

Locate the extracted OTM Pack folder.

![image](https://github.com/user-attachments/assets/05cc1b1e-61ea-4c84-aed3-13410138c748)

Add the folder.

![image](https://github.com/user-attachments/assets/7e4eb095-efaa-4788-8963-a5f75b5dc07e)

The extracted OTM Pack folder is now added to the ISO image.

![image](https://github.com/user-attachments/assets/3329865e-1d81-42e4-81aa-5434232fea58)

Click the next button.

![image](https://github.com/user-attachments/assets/954c800e-aaf5-4b68-a68f-a7071dcdd99d)

This shows up after you click the next button.

![image](https://github.com/user-attachments/assets/bcf1051e-65c9-4289-9ddb-34939108ee9f)

Click the browse icon.

![image](https://github.com/user-attachments/assets/f420c6cb-1838-4f98-a169-259473da6dbc)

Choose the directory where you want to create the ISO image on.

![image](https://github.com/user-attachments/assets/dfc58d47-ccdb-47d7-9040-19e6bfd2234c)

Click "Create Now" to create the ISO image.

![image](https://github.com/user-attachments/assets/60d7866f-de96-45ce-a28f-76e56149ac0f)

It's now creating.

![image](https://github.com/user-attachments/assets/c5d1f5f2-55d6-4f84-aedc-2d7c4991c5b4)

The ISO is now created! Click the exit button to exit AnyBurn.

![image](https://github.com/user-attachments/assets/ea5d5d21-6ba5-4f0a-bd48-a2f7f4a54e30)

You are complete! You can now import the OTM Pack on your VM.
