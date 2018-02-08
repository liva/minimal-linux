# minimal linux

## What's this?

This is the stripped version of linux kernel for learning.

Features are
* fast compilation (only takes 20 seconds on Xeon E3-1275 v5 @ 3.60GHz)
* less source files (1024 .c files)

Limitations are
* only works on x86_64 QEMU
* only supports 8250 serial driver

## compilation

use 'minimalconfig' for configuration. DO NOT GENERATE '.config' FROM 'make' COMMANDS!

```
$ cp minimalconfig .config
$ make -j8 bzImage
```

## make rootfs
```
$ cd (project_root)
$ wget http://busybox.net/downloads/busybox-1.27.2.tar.bz2
$ tar xf busybox-1.27.2.tar.bz2
$ cd busybox
$ make menuconfig
Busybox Settings ---> Build Options --->Build BusyBox as a static binary (no shared libs)
$ make -j8
$ make install
$ cd ../rootfs
$ find . | cpio -o --format=newc > ../rootfs.img
$ cd ..
```

## run
```
qemu-system-x86_64 -kernel arch/x86/boot/bzImage -initrd (project_root)/rootfs.img -append "console=tty0 console=ttyS0,115200 root=/dev/ram rdinit=/bin/sh" -curses
```

You must switch to the serial console monitor with Ctrl+Alt+3.
