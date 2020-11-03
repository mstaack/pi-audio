#Install

```
$ wget https://buildroot.org/downloads/buildroot-2020.08.1.tar.gz
$ tar -xf buildroot-2020.08.1.tar.gz
$ make raspberrypi3_defconfig
$ make savedefconfig
```


# Fresh Build
```
$ make clean && time make all 2>&1 | tee build.log
```

# Logs
```
$ tail -f build.log | grep ">>>"
```

# RT-Patch
```
BR2_LINUX_KERNEL=y
BR2_LINUX_KERNEL_CUSTOM_TARBALL=y
BR2_LINUX_KERNEL_CUSTOM_TARBALL_LOCATION="$(call github,raspberrypi,linux,1c64f4bc22811d2d371b271daa3fb27895a8abdd)/linux-1c64f4bc22811d2d371b271daa3fb27895a8abdd.tar.gz"
BR2_LINUX_KERNEL_DEFCONFIG="bcm2709"
BR2_LINUX_KERNEL_CONFIG_FRAGMENT_FILES="preempt.conf"
$ cat preempt.conf
CONFIG_PREEMPT_RT=y
```

# SD-Card
```
$ sudo dd if=output/images/sdcard.img of=/dev/sdc bs=1M
```
