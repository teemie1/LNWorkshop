# Install Raspiblitz and Synchronize Bitcoin Blockchain

## Copy Bitcoin Blockchain Data

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
