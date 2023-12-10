- Mount **ALL** necessary directories
- ```shell
  arch-chroot /mnt/
  ```
- ```shell
  grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
  ```
- ```shell
  grub-mkconfig -o /boot/grub/grub.cfg
  ```
- `umount -R`
- `exit`
-