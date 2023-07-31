- ```shell
  z download
  wget http://os.archlinuxarm.org/os/ArchLinuxARM-rpi-aarch64-latest.tar.gz
  sudo fdisk -l
  sudo mount /dev/mmcblk0p1 /mnt/pi-boot
  sudo mount /dev/mmcblk0p2 /mnt/pi-root
  sudo bash -c "bsdtar -xpf ArchLinuxARM-rpi-aarch64-latest.tar.gz -C /mnt/pi-root"
  sudo mv -f /mnt/pi-root/boot/* /mnt/pi-boot
  sudo sed -i 's/mmcblk0/mmcblk1/g' /mnt/pi-root/etc/fstab
  sudo umount /mnt/pi-boot /mnt/pi-root
  ```
-