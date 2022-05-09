## Notes to Install Arch

## how to connect to a wifi network in archiso

root@archiso ~ # iwctl

[iwd]# device list

[iwd]# station wlan0 scan

[iwd]# station wlan0 get-networks

[iwd]# station wlan0 connect iballbaton

passphrase: ***********

## Now check if you are connected to the internet

root@archiso# ping google.com

Pinging google.com [2404:6800:4007:808::200e] with 32 bytes of data:

Reply from 2404:6800:4007:808::200e: time=70ms

Reply from 2404:6800:4007:808::200e: time=65ms

Reply from 2404:6800:4007:808::200e: time=60ms

Reply from 2404:6800:4007:808::200e: time=58ms

Ping statistics for 2404:6800:4007:808::200e: 

Packets: Sent = 4, Received = 4, 

Lost = 0 (0% loss), Approximate round trip times in milli-seconds: Minimum = 58ms

Maximum = 70ms, Average = 63ms

![Screenshot (25)](https://user-images.githubusercontent.com/102450738/164955813-d23ae0f5-43c9-4c78-a20f-c9382cf06f63.png)

## Check the partitions

root@archiso# lsblk

cfdisk /dev/

mkfs.fat -F32 /dev/sda1 (512M partition)

mkfs.ext4 /dev/sda2

mount /dev/sda2 /mnt

mkdir /mnt/home

mount /dev/sda2 /mnt/home

lsblk

## 

pacstrap -i /mnt base base-devel linux linux-firmware sudo nano

genfstab -U -p /mnt >> /mnt/etc/fstab

arch-chroot /mnt /bin/bash

nano /etc/locale.gen 

#en_US.UTF-8 UTF-8 (remove the hashtag)

locale-gen

echo "LANG=en_US.UTF-8" > /etc/locale.conf

ln -sf /usr/share/zoneinfo/Asia/Calcutta/ /etc/localtime (change the Asia/Calcutta to your own time zones)

hwclock --systohc --utc

date

echo archPC > /etc/hostname

nano /etc/hosts

127.0.1.1 localhost.localdomain archPC

pacman -S networkmanager

systemctl enable NetworkManager

passwd

pacman -S grub efibootmgr

mkdir /boot/efi

mount /dev/sda1 /boot/efi

lsblk # to check if everything is mounted correctly

grub-install --target=x86_64-efi --bootloader-id=GRUB --efi-directory=/boot/efi --removable

grub-mkconfig -o /boot/grub/grub.cfg

exit

umount -R /mnt 

reboot

## Setup Swap file [optional]

fallocate -l 16G /swapfile

chmod 600 /swapfile

mkswap /swapfile

swapon /swapfile

echo '/swapfile none swap sw 0 0' >> /etc/fstab

free -m

## basic & username things

useradd -m -g users -G wheel -s /bin/bash username

passwd username

EDITOR=nano visudo

# %wheel ALL=(ALL) ALL (uncomment this)

exit

## Basic setup / Install 

sudo pacman -Syyu

sudo pacman -S xorg xorg-xinit xorg-server pulseaudio pulseaudio-alsa git wget curl zip unzip gzip p7zip tar make cmake gcc python-pip node npm go neovim tree man-pages man-db sxhkd bspwm

git clone https://aur.archlinux.org/paru.git
