## Erasing
- Sudo or root needed.
- Will not affect to other partitions nor the partition table
- **DONT DO FOR SSD** SSD memory cells wear out by overwriting them and software block address not match fixex hardware memory cell
- Specific memory cell is not possible to overwrite

Overwriting with zero-bytes the /dev/sda2/:
`dd if=/dev/zero of=/dev/sda2` 

This will erase the first `4096*4096=16MB` and last `512*4096=2MB` of your hard drive, which contain important structures useful for recovery. 

Specifying `count` other than 1 is not useful. If you want to be sure, erase the first block if you want to ensure there is no marks or traces in MBR.

| Command   | Explanation       |
| --------- | ----------------- |
| `if`      | input file        |
| `of`      | output file       |
| `bs`      | block size        |
| `noerror` | no error checking |


## Cloning
### Cloning one partition to another

```Bash
dd if=/dev/sda2 of=/dev/sdb2 bs=64M conv=noerror
```
### Clone hard disk drive 

Clones a hard disk drive "ad0" to "ad1".

```Bash
dd if=/dev/ad0 of=/dev/ad1 bs=64M conv=noerror
```
## Images
### Create disk image

Creates an ISO disk image from: CD, DVD or Blu-Ray

```Bash
blocks=$(isosize -d 2048 /dev/sr0)
```
### Restore a hard disk drive from image

```Bash
dd if=system.img of=[/dev/sdc](https://en.wikipedia.org/wiki//dev/sdc "/dev/sdc") bs=64M conv=noerror
```
### Create an image of the partition

64 MiB block size, creates image of the partition sdb2

```Bash
dd if=/dev/sdb2 of=partition.image bs=64M conv=noerror|Create an image of the partition sdb2, using a 64 MiB block size.
```

### Packing disk image

```Bash
dd if=/dev/hda conv=sync,noerror bs=64K | gzip -c  > diskimage.img.gz
```
