# Install

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
make linux-menuconfig -> PREEMPT Settings
```

# SD-Card
```
$ sudo dd if=output/images/sdcard.img of=/dev/sdc bs=1M
```
