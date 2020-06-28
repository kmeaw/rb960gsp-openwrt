# rb960gsp-openwrt

## How to use?

1. Check out the OpenWrt source tree, branch openwrt-19.07 (153392e20);
2. Apply this patchset;
3. Choose your platform in the configuration system:
```
CONFIG_TARGET_ar71xx=y
CONFIG_TARGET_ar71xx_mikrotik=y
CONFIG_TARGET_ar71xx_mikrotik_DEVICE_rb-nor-flash-16M=y
```
4. Optionally enable the PoE control package:
```
CONFIG_PACKAGE_mtpoe_ctrl=y
```
5. Run `make` to build target images.
6. Set up a BOOTP/TFTP server, serving your openwrt-ar71xx-mikrotik-rb-nor-flash-16M-initramfs-kernel.bin image.
7. Connect the router to your server via ether1, hold the user/reset button and connect the power plug. Wait until the
USER/ACT led starts blinking, then it should stop blinking. Then you can release the button. In a few seconds you should
hear a beep from the bootloader.
8. In about a minute the OpenWrt would boot. In the meanwhile, replug your cable to any of ether2..ether5 ports.
9. SSH as root to 192.168.1.1
10. Transfer the sysupgrade image (openwrt-ar71xx-mikrotik-rb-nor-flash-16M-squashfs-sysupgrade.bin) to your router and
run `sysupgrade openwrt-ar71xx-mikrotik-rb-nor-flash-16M-squashfs-sysupgrade.bin`.
