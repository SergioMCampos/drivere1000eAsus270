# Instructions for installing the driver in Debian

```
sudo make install
sudo modprobe -r e1000e
sudo modprobe e1000e
sudo update-initramfs -u
reboot

```

## Changes with the original

src/netdev.c

```
for (i = 0;; i++) {
    if (e1000_validate_nvm_checksum(&adapter->hw) >= 0)
        break;
    if (i == 2) {
        dev_err(pci_dev_to_dev(pdev),
            "The NVM Checksum Is Not Valid\n");
        err = -EIO;
        goto err_eeprom;
    }
}

´´´
To

´´´
for (i = 0; false; i++) {
´´´