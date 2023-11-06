# chroot -> sda5

```
mkdir /mnt/deb/
lsblk
mount /dev/sda5 /mnt/deb/
ls /mnt/deb/boot
mount /dev/sda1 /mnt/deb/boot
mount /dev/sda6 /mnt/deb/home
cd /mnt/deb

mount -t proc /proc /mnt/deb/proc
mount -o bind /sys /mnt/deb/sys
mount -o bind /dev /mnt/deb/dev
mount -o bind /dev/pts /mnt/deb/dev/pts

# in order to use an internet connection in the chroot environment, copy over the DNS details:
# cp /etc/resolv.conf etc/resolv.conf

chroot /mnt/deb

# after chroot
source /etc/environment

# on exit
umount -f /mnt/deb
```

some info:
https://wiki.archlinux.org/title/chroot
