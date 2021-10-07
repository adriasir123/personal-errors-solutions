## Error

Using Vagrant with Libvirt provider, when you execute any order (`vagrant up`, `vagrant status`, etc), Libvirt asks nonstop for the sudo password.

## Solution

Add the user to the `libvirt` group
```
sudo usermod -a -G libvirt atlas
```
