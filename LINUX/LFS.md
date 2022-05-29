# ---- [ Linux From Scratch] ----

	< [../index.md]

## MODIFY ISO OF LINUX
  * EXTRACT ISO
      mount -t iso9660 -o loop void-linux-***.iso /mnt
      cd /mnt
      mkdir /tmp/linux_custom
      tar cf - . | (cd /tmp/linux_custom; tar xfp -)

   * EXTRACT SQUASHFS
	sudo unsquashfs -f -d /media/extracted_squashfs /tmp/linux_custom/file.squashfs
	sudo mount -t squashfs /tmp/linux_custom/file.squashfs /mnt

   * 

