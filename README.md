# fdemutool

A *NIX tool to assist in the management of floppy images on [floppy disk emulator](https://en.wikipedia.org/wiki/Floppy_disk_hardware_emulator) partitions. 

*More specifically, **1.44Mb Double-Density MS-DOS formatted** images.*

Several of these devices (presumably cheaper ones) don't store
floppy drives as files on an existing file system, but rather just
store the raw data with a 96K offset. It renders the USB-stick
useless for any other purposes.

It also means that you need customized software to access the virtual
floppy disks. What a cheap way to do it! Anyhow, with the information provided on [Gough Lui's blogpost](http://goughlui.com/2013/04/24/review-unbranded-1-44mb-usb-100-floppy-emulator/) this script allows you to perform basic operations such as:

- Create or Copy data to a virtual floppy disk
- Write a floppy disk image to a specific slot (number)
- Mount any virtual floppy disk image slot

It only uses stock tools such as `dd`, `mkfs.msdos` and `mount`.

## Help

*This README document may be out of date - best check the script itself*

```
Mount/Read/Write Floppy Emulation USB sticks

 - USE WITH EXTREME CAUTION - 

Usage: fdemutool <mode> [in] [out] [slot]

Modes:
new  : Create an empty 1.44M disk image in [out]
copy : Copy file or directory [in] to floppy image [out]
       (runs 'new [out]' if [out] doesn't exist)
write: Write [in (floppy image)] to [out (usb image)], slot [slot]
dump : Write [in], [slot] to [out] *TODO*
mount: Mount [in], [slot] to [out]

Example:
  fdemutool copy ~/floppy_disk/ disk1.img
  fdemutool write disk1.img /dev/usb3 1
  fdemutool mount /dev/usb3 1 /mnt/fd

For some interesting information, see
http://goughlui.com/2013/04/24/review-unbranded-1-44mb-usb-100-floppy-emulator/

```

## Requirements

 * `bash`, 
 * `cut` (ships with coreutils)
 * `mkfs.msdos` (usually a symlink to `mkfs.fat`) - ships with `dosfstools`

### A  Note From 2025

`fdemutool` was originally authored in **2015**, but it still has its uses for retro-nerds.
Previously, the script lived on-line in the form of a little gist. After having discovered the original local repo, I figured it deserves better.

## Contact

You can reach me via github: [https://github.com/gammy](https://github.com/gammy)


