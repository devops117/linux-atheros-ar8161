### Build & Install
https://www.linuxquestions.org/questions/linux-networking-3/qualcomm-atheros-ar8171-wake-on-lan-issues-4175491464/#post5387238
```bash
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules_install
rmmod alx
insmod alx.ko
rm /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko
cp alx.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko
```

### Reboot & Run ethtool (should work now)
```
# ethtool -s eth1 wol g
```

WOL should be working now.
