# chroot -> sda5

```
mkdir /mnt/deb/
mount /dev/sda5 /mnt/deb/
ls /mnt/deb/boot
mount /dev/sda1 /mnt/deb/boot
cd /mnt/deb

mount -t proc /proc /mnt/deb/proc
mount -o bind /sys /mnt/deb/sys
mount -o bind /dev /mnt/deb/dev
mount -o bind /dev/pts /mnt/deb/dev/pts

chroot /mnt/deb

# after chroot
source /etc/environment

# on exit
umount -f /mnt/deb