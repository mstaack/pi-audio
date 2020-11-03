# Install

```
$ wget https://buildroot.org/downloads/buildroot-2020.08.1.tar.gz
$ tar -xf buildroot-2020.08.1.tar.gz
$ make raspberrypi3_defconfig
```

# Change Settings

```
$ make menuconfig
```

# Save changes to source defconfig file
```
$ make savedefconfig
```

# RT-Patch
Select PREEMPT Type [Config](https://github.com/raspberrypi/linux/blob/rpi-5.4.y/kernel/Kconfig.preempt)
```
$ make linux-menuconfig
```

# Fresh Build
```
$ make clean && time make all 2>&1 | tee build.log
```

# Logs
```
$ tail -f build.log | grep ">>>"
```

# SD-Card
```
$ sudo dd if=output/images/sdcard.img of=/dev/sdc bs=1M
```
