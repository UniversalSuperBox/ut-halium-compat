# How to install ut-halium-compat

## Patch hybris-boot

There are some changes that have not yet been included into hybris-boot that will need to be in order to correctly test this code. First, cd into `halium/hybris-boot` in your Halium tree, then run the following commands:

Note that this will wipe any changes you've made to files inside of hybris-boot, so be sure to save your work (think fixup-mountpoints).

```
git checkout hal/master
git reset --hard
git pull --rebase https://github.com/UniversalSuperBox/hybris-boot.git halium-ro
git pull --rebase https://github.com/UniversalSuperBox/hybris-boot.git mount-safer2
```

Now, move back into your Halium root and build `hybris-boot` or `hybris-recovery`, whichever you prefer. Flash your new bootable image to your phone.

## Install Ubuntu Touch

Now that you have everything in place, install Ubuntu Touch using [this patched version of rootstock-touch-install](https://github.com/UniversalSuperBox/rootstock-ng/tree/xenial-initchange).

## Patch Ubuntu Touch

From recovery, mount the Ubuntu Touch rootfs.img. Copy the files from the `root/` directory in this repository onto the image, preserving the file structure (`.halium-ro` will be at the root of the image, etc.). Unmount the image, `sync` all filesystems, then reboot. SSH should come up once the system begins booting to help you debug.