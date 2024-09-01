# DebSBuilder
**DebSBuilder** (a.k.a. **Debian System Builder** or **DEBSYSBUILD**) is a script for building Debian systems. It is a command-line interface script.

**DebSBuilder** is only for Debian and Debian-based systems. The script is root-only.
# Releases
## 2 Bookworm
**DebSBuilder 2 Bookworm** (a.k.a. **2.12BO**, **2.12** or **2.bookworm**) is the release of the **DebSBuilder** system builder for Debian 12 (Bookworm).
## 2.13TR
**DebSBuilder 2.13TR** (a.k.a. **2 Trixie**, **2.13** or **2.trixie**) is the upcoming release of the **DebSBuilder** system builder for Debian 13 (Trixie).

# Tool requirements
These are the tools that are required for DebSBuilder, but the script will automatically install these tools.
- update-initramfs (from live-tools) - For updating the initamfs.
- xorriso - For creating the ISO.
- mksquashfs (from squashfs-tools) - For generating the SquashFS.
- debootstrap - For installing the base system.

# ZipOut

**DebSBuilder ZipOut** (called **debsbuilder_zipout** as a shell script, a.k.a. **DSBZIPOUT** or **debS.ISOzip**) is a script for making a Zip archive including your ISO files. Make sure you have the results directory with the **iso_files/** directory.

# Required directories
## isofiles/
**isofiles/** is a directory that includes the ISO files. It is originally from a Debian live ISO, but modified. **isofiles/live/** is empty, but however, it is recommended to keep this directory for initrd, vmllinuz and SquashFS files. 

# Derivatives
## Exactement Builder
**Exactement Builder** (a.k.a. **Quite Builder** in English) is the upcoming **DebSBuillder** derivative for Ubuntu. **Exactement Builder** is a continuation of the DistroShare Ubuntu Imager builder, since their latest version is from 2015.  
### Releases
#### 22J
**Exactement Builder 22J** (a.k.a. **22Jammy**, **JammyJ** or **22.04J**) is the upcoming release of the **Exactement Builder** system builder for Ubuntu 22.04 (Jammy Jellyfish)
#### 24N
**Exactement Builder 24N** (a.k.a. **24Noble** or **24.04N**) is the upcoming release of the **Exactement Builder** system builder for Ubuntu 24.04 (Noble Numbat).
### Notes
Note that snapd is not recommended on the builder. If you want to remove snapd, please [read that here](https://www.simplified.guide/ubuntu/remove-snapd).
If you want to install Firefox as a .deb package instead of using snaps, please [read that here](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04).
## Casysb
**Casysb** (standed as **Custom Arch System Builder**, a.k.a. **ArchSysB**) is the upcoming **DebSBuilder** derivative for Arch Linux.
### Releases
#### 1.2.4.0-beta1
**Casysb 1.2.4.0-beta1** (a.k.a. **1.2.4.0 Beta 1**) is the first beta release for the **Casysb** builder.

# Downloads
## Official (Debian)
### 2 Bookworm
[DebSBuilder 2 Bookworm (313 MB)](https://archive.org/download/debsbuilder/2%20Bookworm/DebSBuilder-2-Bookworm.zip)
