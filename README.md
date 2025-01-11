# Malbian-ISOs

[Malbian ISOs](https://drive.google.com/drive/u/2/folders/1QfVZWiBBJb9UHMUkeOeDuoTZrOpJAYax) are released on google drive.

There are two ISOs available for now. The lightest one is running DWM and the other one is using Xfce as a desktop environment.

## Installation Guide:

After downloading the ISO chech it's Hashes:
**malbian_dwm_alfa-release_x86_64.iso:**
- MD5: 384da83da02274df8659a07d222eae57
- SHA1: c4e37d814ae2a207060398ea1486a307c9db3703
- SHA256: e035c7a6537c7842966eba8056f65f1aa81b0072ae78fac448294d42333edc51

**malbian_xfce_alfa-release_x86_64.iso:**
- MD5: c3fe81d794d4d963217d45865828dbf9
- SHA1: cd227dab604554c2aa1261dd038afbcbded04ec0
- SHA256: 6e7e8aa068fea77fb4fd54c780aed2824971da9c52b984e135640e5e92f0c050 

After verifying the ISO hashes you can now run them in a hypervisor. In our example we're gonna do it for qemu.
First, we need to place the ISO in a combinient place and then create an image:
```shell
cd /var/lib/libvirt/images
sudo mv ~/Downloads/malbian_dwm_alfa-release_x86_64.iso .
sudo qemu-img create -f qcow2 malbianImage.img 30G
```
Now that we have our image created we can simply boot it from the ISO:
```shell
sudo qemu-system-x86_64 -enable-kvm -cdrom /var/lib/libvirt/images/malbian_dwm_alfa-release_x86_64.iso -boot menu=on -drive file=malbianImage.img -m 4G -cpu host -smp 2 -vga virtio -display sdl,gl=on
```

The credentials are **live:evolution**

If you wish to install Malbian OS then just open a terminal and run:
```shell
sudo calamares
```

Complete the instalation and now you can boot from disk running:
```shell
sudo qemu-system-x86_64 -enable-kvm -boot menu=on -drive file=testImage.img -m 4G -cpu host -smp 2 -vga virtio -display sdl,gl=on
```

With that we completed the installation of Malbian DWM (Alfa Release).

The same can be done with the Xfce image.
