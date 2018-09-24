## About Archx

## ![ArchxAsciiLogo](https://raw.githubusercontent.com/virtualdemon/archx/master/screenshot/screenshot.png)

Archx is a archlinux installer script which helps you to install archlinux while your **offline**, further more, it uses **fakepkg** to extract packages from archlinux ISO you booted, in addition, it conveys all packages to **/mnt** , on the other hand you are not forced to use pacstrap script thus you'll have all needed packages installed!

## archlinux offline installer

* Design your hard disk layout with **cfdisk** or **parted** or **gdisk** \(for GPT disks\) or **fdisk**

* Format your partitions with `mkfs` \(make file systems\) \(e.g. : `mkfs.ext4 /dev/sda4` or `mkswap /dev/sda7`\)

* Mount the partitions on **/mnt**

> \(i.e. you have four partitions like below:

| partition | mountpoint |
| :---: | :---: |
| /dev/sda4 | /boot |
| /dev/sda5 | / |
| /dev/sda6 | /home |
| /dev/sda7 | swap area |

> `mount /dev/sda5 /mnt`
>
> `mkdir /mnt/{home,boot}`
>
> `mount /dev/sda6 /mnt/home`
>
> `mount /dev/sda4 /mnt/boot`
>
> `swapon /dev/sda7`
>
> \)

* Download **master branch** zipped file, **unzip** it, cwd to **archx-master** and run **installer** script : \(or [download](https://github.com/virtualdemon/archx/archive/master.zip) it now and use it later\)

`curl -Lsko master.zip https://github.com/virtualdemon/archx/archive/master.zip && unzip master.zip && cd archx-master && ./installer`

> You can read script's source before running it to see what will happen ... : `cat installer`  
> Also if you need to do your chroot customizations automatically, you can run following command in chroot environment : `/tmp/auto_chroot`

* When your customization finished you can `exit` and unmount devices with `umount -R /mnt` then `reboot` system to use your installed archlinux.

* For using pacman \(if you didn't execute auto\_chroot\) as the first time run these commands :

`pacman -Sy`

`pacman-key --init`

`pacman-key --populate archlinux`

`pacman-key --refresh-keys`

* To use the AUR packages just take a look at [trizen/trizen](https://github.com/trizen/trizen)



