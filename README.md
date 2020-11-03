## Setup

### Download & Setup Buildroot

```
$ wget https://buildroot.org/downloads/buildroot-2020.08.1.tar.gz
$ tar -xf buildroot-2020.08.1.tar.gz
$ make raspberrypi3_defconfig
```

### Make Changes

```
$ make menuconfig
```

### Save minimal changes to source defconfig file (./config/raspberrypi3_defconfig)
```
$ make savedefconfig
```

### RT-Patch.
Select PREEMPT Type [Config](https://github.com/raspberrypi/linux/blob/rpi-5.4.y/kernel/Kconfig.preempt) ?
```
$ make linux-menuconfig
```

### Change Kernel Configuration to use changes?!
current:
```
BR2_LINUX_KERNEL_CUSTOM_TARBALL=y
BR2_LINUX_KERNEL_CUSTOM_TARBALL_LOCATION="$(call github,raspberrypi,linux,1c64f4bc22811d2d371b271daa3fb27895a8abdd)/linux-1c64f4bc22811d2d371b271daa3fb27895a8abdd.tar.gz"
BR2_LINUX_KERNEL_DEFCONFIG="bcm2709"
```
safe linux config somewhere?! select changed config?
use BR2_LINUX_KERNEL_CONFIG_FRAGMENT_FILES ?

### Fresh Build
```
$ make clean && time make all 2>&1 | tee build.log
```

### Main Logs
```
$ tail -f build.log | grep ">>>"
```

### SD-Card
```
$ sudo dd if=output/images/sdcard.img of=/dev/sdc bs=1M
```
