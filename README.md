## About Archx
![ArchxAsciiLogo](https://raw.githubusercontent.com/virtualdemon/archx/master/screenshot/screenshot.png)

Archx is a ArchLinux installer script which helps you to install ArchLinux while your offline, further more, it uses **fakepkg** to extract packages from ArchLinux ISO you booted, in addition, it conveys all packages to **/mnt** , on the other hand you are not forced to use Pacstrap script thus you'll have all needed packages installed!

## ArchLinux offline installer

 1. Design your hard disk layout with **cfdisk** or **parted** or **gdisk** (for GPT disks) or **fdisk**

 2. Format your partitions with `mkfs` (make file systems) (e.g. : `mkfs.ext4 /dev/sda4` or `mkswap /dev/sda7`)

 3. Mount the partitions on **/mnt** 
> (i.e. you have four partitions like below:

|partition|mountpoint|
|--|--|
|/dev/sda4|/boot|
|/dev/sda5|/|
|/dev/sda6|/home|
|/dev/sda7|swap area|
    

> )

4. Download **fakepkg** script :
    
    **`curl -s -o fakepkg https://gitlab.com/virtualdemon/archx/raw/master/fakepkg && chmod +x fakepkg`** 

5. Extract and install packages on /mnt : [ Rebuilding live system installed packages (with fakepkg) ]
    
    **`curl -s -o installer https://gitlab.com/virtualdemon/archx/raw/master/installer && chmod +x installer && ./installer`**  

6. You can read script's source before running it to see what will happen ... : `cat installer`  
Also if you need to do your chroot customizations automatically, you can run following command in chroot environment :
> if you were connected to internet in install duration it's already downloaded at '/mnt/tmp/auto_chroot' so just run it : `/tmp/auto_chroot`

    `curl -s -o auto_chroot https://gitlab.com/virtualdemon/archx/raw/master/auto_chroot && chmod +x auto_chroot && ./auto_chroot`

7. When your customization finished you can `exit` and unmount devices with `umount -R /mnt` then `reboot` system to use your installed ArchLinux.

8. For using pacman (if you didn't execute auto_chroot) as the first time run these commands :  
`pacman -Sy`  
`pacman-key --init`  
`pacman-key --populate archlinux`  
`pacman-key --refresh-keys`

9. To use the AUR packages just take a look at [trizen/trizen](https://github.com/trizen/trizen)
