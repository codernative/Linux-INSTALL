
## For the key issues

`gpg --keyserver pool.sks-keyservers.net --recv-keys 95D2E9AB8740D8046387FD151A09227B1F435A33`


## Install reflector for Updating fast mirrorlist

`# sudo pacman -Syy reflector`
`# reflector -c india -a 6 --sort rate --save /etc/pacman.d/mirrorlist`


## Wifi Settings
1. `# iwctl`
2. `# wsc list` to find wifi device
3. `# wsc wlan0* push-button`
4. `# station wlan0* scan`
5. `# staton wlan0* get-networks`
6. `# station wlan0* connect elrod*`


## BIOS or EFI

`# ls /sys/firmware/efi/efivars` if cannot access it BIOS


## Partition of disk

`# gdisk /dev/sda` for partitioning EFI partition.

*commant : n*
*partition num : enter*
*first : enter*
*last : +500M*
*type :ef00*

https://wiki.archlinux.org/index.php/GPT_fdisk


## Make file system

`# mkfs.fat -F32 /dev/sda1` for efi

`# mkfs.ext4 /dev/sda2*` root or home


## Mount

`# mount /dev/sda2 /mnt`

`# mkdir -p /mnt/boot/efi`

`# mount /dev/sda1 /mnt/boot/efi`


## Install package using _pacstrap_

`# pacstrap /mnt base linux linux-firmware intel-ucode vim` basic installation


## Generating fstab

`# genfstab -U /mnt >> /mnt/etc/fstab`


**chroot to arch**

`# arch-chroot /mnt`


## Swapfile

`# dd if=/dev/zero of=swapfile bs=1G count=4`

`# chmod 600 /swapfile` permission

`# mkswap /swapfile`

`# swapon /swapfile`

`# vim /etc/fstab` 

_/swapfile none swap default 0 0 _


## Time and date and language

`# ln -sf /usr/share/zoneinfo/Asia/Riyad /etc/localtime`

`# hwclock --systohc` update hardware clock

Edit `/etc/locale.gen` and uncomment en_US.UTF-8 UTF-8 and other needed locales
Generate the locales by running: 

`# locale-gen`

`# echo "LANG=en_US.UTF-8" >>  /etc/locale.conf`

`# vim /etc/hostname` your host name *eg: MyBrokenHP*

`# vim /etc/hosts` 

*127.0.0.1	localhost*

*::1		localhost*

*127.0.1.1	myhostname.localdomain	myhostname*


**Create password**

`# psswd`


##Install requred packages

`# pacman -S grub efibootmgr networkmanager networkmanger-applet os-prober dialog reflector wpa_supplicant mtools dosfstools base-devel linux-headers git bluez bluez-utils alsa-utils pulseaudio pulseaudio-bluetooth acpi acpi_call xf86-video-intel nvidia nvidia-utils nvidia-settings xorg`


**Extra some packages**

`lightdm` : display manager

`cups` : printer

`feh` : image viewer and set background

`zsh` : zsh shell


## Install GRUB

`# grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=GRUB`

`# grub-mkconfig -o /boot/grub/grub.cfg`

https://wiki.archlinux.org/index.php/GRUB


### Enable Network Manager

`# systemctl enable Networkmanger`

`# nmtui` select network


## Add user

`# useradd -mG wheel ckajeer`

`# passwd ckajeer`

`# usermod -c `Ajeer ck` ckajeer`

`# EDTOR=vim visudo` uncomment *%wheel ALL=(ALL) ALL


## EXIT

`# exit`

`# umount -a`

`# reboot`

