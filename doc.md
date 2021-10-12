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
