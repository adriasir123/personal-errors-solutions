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

Use vsftpd with chroot, change home directory of ftp users. use Cx Explorer on Android to access FTP server.
