## Problem

Using Vagrant with Libvirt provider, when you execute any order (`vagrant up`, `vagrant status`, etc), Libvirt asks nonstop for the sudo password.

## Solution

Add the user to the `libvirt` group
```
sudo usermod -a -G libvirt atlas
```

## Problem

I want to be able to share a specific directory on my Raspberry Pi over the Network, and from an Android phone, upload pictures and files to it.

## Solution

https://www.linuxquestions.org/questions/linux-newbie-8/how-could-i-upload-pictures-and-videos-from-android-phone-to-a-remote-directory-on-my-raspberry-with-debian-10-a-4175701848/#post6291362


## Problem

Using vagrant-libvirt, once a VM is created, if you try to modify the network configuration (for example, creating additional interfaces), it won't work, and Vagrant understand that process somehow as "provisioning". Using --provision won't update the interfaces information either.

Only workaround found it's to vagrant destroy and up again. If you don't want to lose your data, a workaround is found here https://stackoverflow.com/questions/43411734/correct-way-to-back-up-and-restore-vagrant-box-variable-vvv/54446363#54446363.

Basically you create a backup box, and then vagrant destroy and up the same machine, but using the backup box.

## Solution

Not found one yet.



## Problem

A logical volume with LVM is running out of space.

## Solution

https://www.linuxtechi.com/extend-lvm-partitions/


## Problem

Disk file qcow2 of VM Vagrant Libvirt is running out of space and I need to resize it (Rocky8 VM).

## Solution

```
sudo qemu-img resize /var/lib/libvirt/images/escenario-libvirt_hera.img +1G
sudo dnf install cloud-utils-growpart
sudo growpart /dev/vda 1
sudo xfs_growfs /
```

Check:
```
lsblk
df -Th
```
