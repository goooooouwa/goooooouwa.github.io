---
title: Arch Linux Installation Steps
category: computer
tags: archlinux
published: true
---
## 1 Pre-installation

### 1.1 download iso

Visit the [Download](https://archlinux.org/download/) page and download the ISO file.

### 1.3 make bootable usb

### 1.4 boot live environment

Note: Arch Linux installation images do not support Secure Boot. You will need to disable Secure Boot to boot the installation medium.

### 1.5 Set the console keyboard layout and font

`# loadkeys us`

### 1.6 Verify the boot mode

`# cat /sys/firmware/efi/fw_platform_size`

If the command returns 64, the system is booted in UEFI mode and has a 64-bit x64 UEFI.

### 1.7 Connect to the internet

Ensure your network interface is listed and enabled

`# ip link`

Check ip address
`# ip address`

Connect to the network:
- Ethernet -- plug in the cable.
- Wi-Fi -- authenticate to the wireless network using iwctl.

Use iwctl to connect to WiFi:

First, if you do not know your wireless device name, list all Wi-Fi devices:
[iwd]# device list

Then, to initiate a scan for networks (note that this command will not output anything):
[iwd]# station name scan

You can then list all available networks:
[iwd]# station name get-networks

Finally, to connect to a network:
[iwd]# station name connect SSID

DHCP should be automatically configured by Ethernet or WiFi network connection.

The connection may be verified with ping:

`# ping archlinux.org`

### 1.8 Update the system clock

`# timedatectl`

### 1.9 Partition the disks

To identify these devices, use lsblk or fdisk.

`# fdisk -l`

Use a partitioning tool like fdisk to modify partition tables. For example:

`# fdisk /dev/the_disk_to_be_partitioned (e.g. /dev/sda)`

Within fdisk:

1. `g` (create a new GPT table)

2. create EFI partition

`n` (create a new partition for EFI)

`Enter` (to accept default partition number 1)

`Enter` (to accept default first sector)

`+1G` (to add 1GB space for EFI boot partition)

3. create root partition

`n` (create a new partition for root)

`Enter` (to accept default partition number 2)

`Enter` (to accept default first sector)

`Enter` (to accept default last sector to use the remaining of the disk space)


4. `w` (write partitions to disk)

### 1.10 Format the partitions

To create an Ext4 file system on /dev/root_partition, run:

`# mkfs.ext4 /dev/root_partition (e.g. /dev/sda2)`

If you created an EFI system partition, format it to FAT32 using mkfs.fat(8).

`# mkfs.fat -F 32 /dev/efi_system_partition (e.g. /dev/sda1)`

1.11 Mount the file systems

Mount the root volume to /mnt. For example, if the root volume is /dev/root_partition:

`# mount /dev/root_partition /mnt`

For UEFI systems, mount the EFI system partition:

`# mount --mkdir /dev/efi_system_partition /mnt/boot`

## 2. Installation

### 2.1 Select the mirrors

On the live system, after connecting to the internet, reflector updates the mirror list by choosing 20 most recently synchronized HTTPS mirrors and sorting them by download rate.

`# reflector`

### 2.2 Install essential packages

Use the pacstrap(8) script to install the base package, Linux kernel and firmware for common hardware:

`# pacstrap -K /mnt base linux linux-firmware networkmanager grub efibootmgr os-prober sudo amd-ucode (or intel-ucode) vi vim git man-db man-pages texinfo`

To install other packages or package groups, append the names to the pacstrap command above (space separated) or use pacman to install them while chrooted into the new system. In particular, consider installing:

- CPU microcode updates—amd-ucode or intel-ucode—for hardware bug and security fixes,
- software necessary for networking (e.g. a network manager or a standalone DHCP client, authentication software for Wi-Fi, ModemManager for mobile broadband connections),
- a console text editor (e.g nano) to allow editing configuration files from the console,
- packages for accessing documentation in man and info pages: man-db, man-pages and texinfo.
- a bootloader

## 3. Configure the system

### 3.1 Fstab

Generate an fstab file

`# genfstab -U /mnt >> /mnt/etc/fstab`

### 3.2 Chroot

Change root into the new system:

`# arch-chroot /mnt`

### 3.3 Time

Set the time zone:

`# ln -sf /usr/share/zoneinfo/Region/City /etc/localtime`

e.g. `# ln -sf /usr/share/zoneinfo/US/Pacific /etc/localtime`

Run hwclock(8) to generate /etc/adjtime:

`# hwclock --systohc`

### 3.4 Localization

Edit `/etc/locale.gen` and uncomment `en_US.UTF-8 UTF-8` and other needed UTF-8 locales (e.g. `zh_CN.UTF-8 UTF-8`). Generate the locales by running:

`# locale-gen`

Create the locale.conf(5) file, and set the LANG variable accordingly:

```
# /etc/locale.conf
LANG=en_US.UTF-8
```

If you set the console keyboard layout, make the changes persistent in vconsole.conf(5):

```
# /etc/vconsole.conf
KEYMAP=us
```

### 3.5 Network configuration

Create the hostname file:

```
# /etc/hostname
yourhostname (e.g. arch-linux)
```

Complete the network configuration for the newly installed environment by installing suitable network management software, configuring it if necessary and enabling its systemd unit so that it starts at boot.

Here I choose NetworkManager.

Install NetworkManager (if not installed already)

`# pacman -S networkmanager`

Enable NetworkManager.service

`# systemctl enable NetworkManager.service`

### 3.7 Root password

passwd

### 3.8 Boot loader

Choose and install a Linux-capable boot loader.

Here I choose GRUB.

Install GRUB (if not installed already)

`# pacman -S grub efibootmgr`

Execute the following command to install the GRUB EFI application `grubx64.efi` to `esp/EFI/GRUB/` and install its modules to `/boot/grub/x86_64-efi/`.

Note: `esp` denotes the mountpoint of the EFI system partition aka ESP, one common mountpoint for EFI is `/boot`.

`# grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB`

Generate the main configuration file

`# grub-mkconfig -o /boot/grub/grub.cfg`

Detecting other operating systems

To have `grub-mkconfig` search for other installed systems and automatically add them to the menu, install the `os-prober` package and mount the partitions from which the other systems boot.

`# pacman -S os-prober`

Then re-run grub-mkconfig.

`# grub-mkconfig -o /boot/grub/grub.cfg`

If you get the following output: Warning: os-prober will not be executed to detect other bootable partitions then edit `/etc/default/grub` and add/uncomment:

`GRUB_DISABLE_OS_PROBER=false`

## 4 Reboot

Exit the chroot environment by typing `exit` or pressing `Ctrl+d`.

Optionally manually unmount all the partitions with `umount -R /mnt`: this allows noticing any "busy" partitions, and finding the cause with fuser(1).

Finally, restart the machine by typing `reboot`.

## 5 Post-installation

### 5.1 System administration

Create user

`# useradd -m -G wheel greg`

`# passwd greg`

Add user to sudo group

Run `visudo` and uncomment line `"%wheel ALL=(ALL) ALL"`

### 5.7 Network setup

Use `nmcli` to connect to Wi-Fi

`nmcli` examples:

List nearby Wi-Fi networks:

`# nmcli device wifi list`

Connect to a Wi-Fi network:

`# nmcli device wifi connect SSID_or_BSSID password password`

### 5.4 Graphical user interface

Install KDE

`# pacman -S plasma-meta kde-applications-meta`

keep pressing Enter to accept default packages to follow through the installation process (or choose your preferred packages)

Install sddm window manager

`# pacman -S sddm`

Enable sddm service

`# systemctl enable sddm.service`

### 5.5 Install AUR helper

```
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/yay-git.git
cd yay-git
makepkg -si
```

### 5.6 Install Google Chrome using AUR helper

To install Google Chrome in Arch Linux using yay:

`yay -S google-chrome`

Keep pressing `Enter` to follow through the installation process (or choose your preferred packages).

Keep in mind that unlike pacman, yay shouldn’t be run with “sudo” privilege.
