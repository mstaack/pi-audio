1. Download & Setup Buildroot

```
$ wget https://buildroot.org/downloads/buildroot-2020.08.1.tar.gz
$ tar -xf buildroot-2020.08.1.tar.gz
$ make raspberrypi3_defconfig
```

2. Make Changes

```
$ make menuconfig
```

3 Save minimal changes to source defconfig file (./config/raspberrypi3_defconfig)
```
$ make savedefconfig
```

4. RT-Patch
Select PREEMPT Type [Config](https://github.com/raspberrypi/linux/blob/rpi-5.4.y/kernel/Kconfig.preempt) ?
```
$ make linux-menuconfig
```

5. Change Kernel Configuration to use changes?!


6. Fresh Build
```
$ make clean && time make all 2>&1 | tee build.log
```

7. Logs
```
$ tail -f build.log | grep ">>>"
```

8. SD-Card
```
$ sudo dd if=output/images/sdcard.img of=/dev/sdc bs=1M
```
