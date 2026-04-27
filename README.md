# NOTICE: THIS PROJECT HAS MOVED TO [CODEBERG][1]
# Last updated at codeberg on 2025-Jul-15

# thumby

A bootable thumbdrive image for rescue and maintenance.

* This is a proof of concept for PLL, s6-smj, and mdevd-as-an-admin.

* This is a general x86-64 kernel and root filesystem.

* Editors: e3 emacs hexedit hyx

* Net: bing bmon bwm-ng bwping iftop iptraf-ng macchanger mtr nast netcat traceroute trafshow dnscrypt-proxy ntftables mosh ntp ssh rsync telnet wget whois rtorrent iwd ip lynx

* System: earlyoom hdparm sdparm lspci lsusb lsblk smartmon cryptsetup inotify gpm

* Filesystems: f2fs ext4 xfs vfat ntfs

* Mail: mutt

* Misc: bash fastfetch reptyr strace execline nasm dialog ascii-invaders

## PLL

* It uses PLL to load the kernel with an internal initmpfs from partition one.

* The first time it boots, it will create a new partition three as an F2FS filesystem, consuming all free space on the drive.

* It then mounts the SquashFS filesystem in partition two as the `lower`, and partition three as the `upper`, of an OverlayFS, and mounts that as the new root.

* It then calls `switch_root` to boot into the new root.

## `s6-smj`

* `/usr/libexec/init` then initializes /run, and 's6' is started as PID 1

* s6 initializes the rest of the system and starts daemons such as mdevd, mingetty and sshd.

## mdevd-as-an-admin

* mdevd brings up the network and other media


## USE

* the root password is `thumby`

[1]: https://codeberg.org/smj/thumby
