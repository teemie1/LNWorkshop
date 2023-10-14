# Install Raspiblitz and Synchronize Bitcoin Blockchain

## Prepare Bitcoin Blockchain Data

### Create ext4 Filesystem

~~~
$ lsblk

$ sudo fdisk /dev/[DISK NAME]
# p
# d
# w

$ sudo fdisk /dev/[DISK NAME]
# c

$ sudo mkfs.ext4 /dev/sdc1

~~~

### Copy Blockchain Data

~~~
$ sudo rsync -a --info=progress2 /media/tee/BLOCKCHAIN/bitcoin /media/tee/BLOCKCHAIN1
$ rsync -a --info=progress2 --delete ${pathTemplateHDD}/* /mnt/hdd2
~~~
