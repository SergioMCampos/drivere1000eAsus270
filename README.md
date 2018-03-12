# Instructions for installing the driver in Debian

```
sudo make install
sudo modprobe -r e1000e
sudo modprobe e1000e
sudo update-initramfs -u
reboot

```
