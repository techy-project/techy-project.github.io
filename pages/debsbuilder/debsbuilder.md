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

# Downloads
## 2 Bookworm
[DebSBuilder 2 Bookworm (313 MB)](https://archive.org/download/debsbuilder/2%20Bookworm/DebSBuilder-2-Bookworm.zip)
