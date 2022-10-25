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

## Solution

Only workaround found it's to vagrant destroy and up again. If you don't want to lose your data, a workaround is found here (backing up and restoring): https://stackoverflow.com/questions/43411734/correct-way-to-back-up-and-restore-vagrant-box-variable-vvv/54446363#54446363.

Basically you create a backup box, and then vagrant destroy and up the same machine, but using the backup box.

If you want to speciy a VM name, run:
```
vagrant package name --output ./namev1.box
```



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



## Problem

Default qcow2 file (20G) of vagrant VM for Oracle too small, I need to resize it.

## Solution

Stop the VM:

```shell
vagrant halt servidororacle
```

Resize the disk file:

```shell
virsh -c qemu:///system vol-resize p1-bd-alumno1_servidororacle.img 50G --pool default
```

Resize the partition and filesystem:

```shell
echo ", +" | sudo sfdisk -N 1 /dev/vda --no-reread
sudo partprobe
sudo resize2fs /dev/vda1
```








## Problem

SSD not recognized during the Debian 11.5 installation (partitioning step).

## Solution

Change SATA settings in BIOS from RST to AHCI.



## Problem

```
Unable to install GRUB in dummy
Executing 'grub-install dummy' failed.
This is a fatal error.
```

## Solution

The EFI partition must NOT be inside LVM. It HAS TO BE a physical partition, otherwise the debian installer won't find the EFI partition inside LVM.  
GRUB is installed in EFI.



## Problem

WiFi not working on Debian 11.5.

## Solution

https://miloserdov.org/?p=5930

```
sudo apt install bc module-assistant build-essential dkms
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
sudo m-a prepare
sudo ./dkms-install.sh
```

Next, restart.
