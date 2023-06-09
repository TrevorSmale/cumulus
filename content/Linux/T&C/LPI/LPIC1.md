---
title: "LPIC 1 Certification"
date: 2023-05-29T18:31:10-04:00
draft: false
---

{{< panel title="Update Log" style="success" >}}

* 2023 06 05 - Initial Commit

{{< /panel >}}

{{< lead >}}

# LPIC-1 Notes

## Objectives

## 101.1 Determine and configure hardware settings

Should be able to determine and configure fundamental system hardware.

### Key knowledge Areas

* Enable and disable integrated peripherals.
* Differentiate between various types of mass storage devices.
* Determine hardware resources for devices.
* Tools and utilities to list various hardware information (e.g. `lsub`, lspci`, etc.).
* Tools and utilities to manipulate USB devices.
* Conceptual understanding of `sysfs`, `udev` and `dbus`.

### Partial list of used files, terms and utilities

* `/sys`
* `/proc`
* `/dev`
* `modprobe`
* `lsmod`
* `lspci`
* `lsusb`

### TOC

* Must know hardware concepts
* Linux filesystem & external devices
* Get information about hardware
* System modules

### Must know hardware concepts

* __IRQ__ (_Interrupt Request_): Hardware signal sent to the processor that temporarily stops a running program and allows a special program, an _interrupt handler_, to run instead. Hardware interrupts are used to handle events such as receiving data from a modem/network card, key presses, or mouse movements.
  * `/proc/interrupts`
* __DMA__ (_Direct memory Access): Feature that allows certain hardware subsystems to access main system memory (RAM) independent of the central processing unit (CPU). CPU first inititates the transfer, then it does other operations while the transfer is in progress and it finally receives an _interrupt_ from the DMA controller (DMAC) when the operation is done.
  * `/proc/dma`
* __I/O Ports/Addresses__: Unique locations in memory reserved for communications between CPU and specific physical hardware devices.
  * `/proc/ioports`
* __coldplug/hotplug__: Devices that should be unplugged when system is off (cold) or on (hot).

### Linux file system & external devices

* __Sysfs__ (`/sys`): Pseudo file system that exports information about various kernel subsystems, hardware devices, and associated device drivers from the kernel's device model to user space through virutal files.
* __D-Bus__ (_Desktop Bus_): Software bus, _Inter Process Communication (IPC)_ and _Remote Procedure Call (RPC)_ mechanism that allows communication between multiple processes running concurrently on the same machine. 
* __udev__ (`/dev`): Userspace system that enables the OS administrator to register userspace handlers for events. The events received by _udev_'s daemon are mainly generated by the (Linux) kernel in response to physical events relating to peripheral devices. As such, _udev_'s main purpose is to act upon peripheral detection and hot-plugging, including actions that return control to the kernel. It manages device nodes in the `/dev` directory by adding, symlinking and renaming them. _udev_ replaces the functionality of both _hotplug_ and _hwdetect_.
  * e.g. Every time we connect a USB media device, files will be created to link the device with the file system, and multiple references too for example `cd /dev/disk && ls -l`.

### Get information about hardware

* `lspci`: Show information about PCI buses and connected devices.
  * `-v`/`-vv`: More verbose.
  * `-s`: Information about specific device.
* `lsusb`: Show information about buses and USB devices connected.
  * `-v`/`-vv`/`-s`
  * `-t`: Information as a tree and details about USB port.

### System modules

Modules are part of the kernel that we can activate/deactivate to add/remove functionalities. They are very coupled to drivers.

Those are files that end with the extension `.ko` that are stored at `/lib/modules/kernel_version`.

### Commands for system modules

* `lsmod`: Show modules loaded in the system.
* `modinfo`: Show information about a module.
* `insmod`: Load a `.ko` file to the system.
* `rmmod`: Remove a module from the system.
  * `-w`: Wait for it's not being used.
  * `-f`: Force removal.
* `modprobe`: Load or remove modules and resolve dependencies.
  * `-f`: Force load even if kernel version is mismatched.
  * `-r`: Remove module.
  * `-v`: Verbose.

If you are looking for an specific module: `lsmod | grep floppy`.

## 101.2

### 2. Boot the system

Should be able to guide the system through the booting process.

### Key knowledge areas

* Provide common commands to the boot loader and options to the kernel at boot time.
* Demonstrate knowledge of the boot sequence from BIOS/UEFI to boot completion.
* Understanding of _SysVinit_ and _systemd_.
* Awareness of _Upstart_.
* Check boot events in the log files.

### Partial list of used files, terms and utilities

* dmesg
* journalctl
* BIOS/UEFI
* bootloader
* kernel
* initramfs
* init
* SysVinit
* systemd

### TOC

* BIOS
* EFI/UEFI
* Boot sequence
* MBR: Master Boot Record
* GPT: GUID Partition Table
* GRUB 2
* Boot Processes
  * SysVinit
  * systemd
  * Upstar
* dmesg
* initramfs & initrd

### BIOS

Firmware in ROM/PROM, that works as a basic I/O system.

It consists of two fundamental parts:

* __Setup__: configure options.
* __POST__: assess correct functionality of important components for startup.

### EFI/UEFI

Unified Extensible Firmware Interface. It is a specification that defines a software interface between an OS and platform firmware, replacing the legacy BIOS (but providing support for it).

Intel developed the original EFI specifications. In 2005, UEFI deprecated EFI 1.10, and its specification is managed by the _Unified EFI Forum_.

### Advantages

* Backward and forward compatibility.
* Support for legacy BIOS systems.
* Ability to use large disk partitions (over 2TB) with a GUID partition table (GPT).
* Friendly and flexible environment pre-OS environment, including network capability, GUI and multi language.
* Modular design.
* Secure Boot option.

### Disadvantages

* Higher abstraction layer and ability to run UEFI applications opens the doors to rootkit.
* Many argue that UEFI introduces an unnecessary complexity that won't be used by OS anyway. Not many mainline OSes take advantage of CPU-independent drivers nor the flexible and modular design, and every OS needs a native driver.

### Boot sequence

1. BIOS firmware / UEFI.
2. POST checks for hardware working properly.
3. Look for a _Boot loader_ depending on the order we configured the devices boot sequence.
  * If using BIOS, it reads the first sector of the MBR driver where the code for searching the bootloader is stored.
  * IF using UEFI, it executed the bootloader  that is stored in a special partition (ESP).

### Boot loader

When a computer is turned off, its software‍—‌including operating systems, application code, and data‍—‌remains stored on non-volatile memory.

When the computer is powered on, it typically does not have an operating system or its loader in random-access memory (RAM). The computer first executes a relatively small program stored in read-only memory (ROM) along with a small amount of needed data, to access the nonvolatile device or devices from which the operating system programs and data can be loaded into RAM.

The small program that starts this sequence is known as a _bootstrap loader, bootstrap or boot loader_. This small program's only job is to load other data and programs which are then executed from RAM. Often, multiple-stage boot loaders are used, during which several programs of increasing complexity load one after the other in a process of chain loading.

### MBR: Master Boot Record

Special type of _boot sector_ at the very beginning of partitioned computer mass storage devices. The concept of MBRs was publicly introduced in 1983 with PC DOS 2.0.

The MBR holds the information on how the logical partitions, containing file systems, are organized on that medium. The MBR also contains executable code to function as a loder for the installed operating system, usually referred to as a _boot loader_.

The organization of the partition table in the MBR limits the maximum addressable storage aspace of a partitioned disk to _2 TiB_. Therefore, the MBR-based partitioning scheme is in the process of being supersedded by the _GUID Partition Table (GPT)_ scheme in new computers, which can coexist with an MBR in order to provide some limited form of backward compatibility for older systems.

MBRs are note present on non-partitioned media such as floppies or other storage devices configured to behave as such.

### GUID

Standard for the layout of partition tables of a physical computer storage device, such as a HDD or SSD, using _universally unique identifiers_, which are also known as _Globally Unique Identifiers (GUIDs)_. Forming part of the _UEFI_ standard, it is nevertheless also used for some BIOS systems, because of the limitations of MBR partition tables. GUID can support up to _9.4 ZiB_.

All modern PC OS support GPT. Some, including macOS and Microsoft Windows on the x86 architecture, support booting from GPT partitions only on systems with EFI firmware, but FreeBSD and most Linux distributions can boot from GPT partitions on systems with either firmware interface, legacy BIOS or modern EFI.

```
parted -l
```

### GRUB 2 (GRand Unified Bootloader)

GRUB 2 is the default free boot loader for many linux distributions. As the computer starts, GRUB 2 either presents a menu and awaits user input or automatically transfers control to an operating system kernel. It has completely rewritten GRUB to provide the user significantly increased flexibility and performance.

### Boot Processes

Once the grub boot loader loads the kernel and it has finished its startup procedure, it will hand over control to a startup manager.

### SysVinit

On systems based on SysVinit, __init__ is the first process that is executed once the Linux kernel loads. This process is responsible for coordinating the start of the rest of the system services, configuring the user environment and essentialy bringing the system to a functional state.

* File `/etc/inittab` contains basic configuration.

* Different execution levels are defined, and __rc__ script is invoked (`/etc/rc.d` or `/etc/init.d`) with a specific execution level.

* __rc__ executes the files in `/etc/rc<level>.d/` by numeric order. Those files are links that start with `S` (start) or `K` (stop) and that point to a script in `/etc/init.d`.


### systemd

_systemd_ is a suite of basic building blocks for a Linux system. It provides a system and service manager that runs as PID 1 and starts the rest of the system. It uses configuration files for each service/unity to manage.

The main command used to introspect and control _systemd_ is `systemctl`.

* `systemctl status`
* `systemctl list-units [--type=service]`
* `systemctl --failed`
* `systemctl status <pid|unit>`
* `systemctl start/stop/status unit[.service]`
* `systemctl enable/disavble`

_systemd_ uses its own log manager `journalctl`.

* `journalctl`
  * `-S`: since.
  * `-U`: until.
  * `YYYY-MM-DD [HH:MM:SS]]`, `yesterday`, `today`, `tomorrow`, `N day ago`, `+/- NhMmin` (i.e `-1h15min`)
  * `-u <unit>`
  * `-k`: kernel.
  * `-p`: emerg, alert, critc, err, warning, notice, info, debug.


### Upstar

> Maintenance mode only. No new features are being developed and general advice would be move over to another minimal init system or systemd.

Upstar is an event-based replacement for the `/sbin/init` daemon which handles starting of tasks and services during boot, stopping them during shutdown and supervising them while the system is running.

### `dmesg`

You can use `dmesg` to see boot logs (drivers and operating system loading).

* `-T`: more explit time data.
* `-k`: kernel.
* `-l` filter by type of alert.
* `H`: filter with colors.

### initramfs

`initramfs`: Initial RAM File System & `initrd`: Initial RAM Disk

Scheme for loading a temporary root file system into memory, which may be used as part of the Linux startup process. `initrd` and `initramfs` refer to two different methods of achieving this. Both are commonly used to make preparations before the real root file system can be mounted.

Many Linux distros ship a single, genering Linux kernel image, specifically to boot on a wide variety of hardware. The device drivers for this generic kernel image are included as loadable kernel modules because statically compiling many drivers into one kernel causes the kernel image to be much larger, perhaps too large to boot on computers with limited memory. This then raises the problem of detecting and loading the modules necessary to mount the root file system at boot time, or for that matter, deducing where or what the root file system id.

To further complicate matters, the root file system may be on a software RAID volume, LVM, NFS, or an encrypted partition. All of these require special preparations to mount.

Another complication is kernel support for hibernation, which suspends the computer to disk by dumping an image of the entire contents of memory to a swap partition or a regular file, then powering off. On next boot, this image has to be made accessible before it can be loaded back into memory.

To avoid having to hardcore handling for so many special cases into the kernel, an initial boot stage with a temporary root file-system, now dubbed _early user space_, is used. This root file system can contain user-space helpers which do the hardware detection, module loading and device discovery necessary to get the real root file-system mounted.

You can find it in the GRUB configuration file in a similar way:

```
initrd /boot/initrd.img-<version>-amd64
```

## 101.3 Change runlevels / boot targets and shutdown or reboot system

Should be able to manage the SysVinit runlevel or systemd boot target of the system. This objective includes changing to single user mode, shutdown or rebooting the system.

Should be able to alert users before switching runlevels / boot targets and properly terminate processes.

### Key knowledge areas

* Set the default runlevel or boot target.
* Change between runlevels / boot targets including single user mode.
* Shutdown and reboot from the command line.
* Alert users before switching runlevels / boot targets or other major system events.
* properly terminate processes.
* Awareness of acpid.

### Partial list of used files, terms and utilities

* `/etc/inittab`
* shutdown
* init
* `/etc/init.d/`
* telint
* systemd
* systemctl
* `/etc/systemd/`
* `/user/lib/systemd`
* wall

### TOC

* Terminal commands
* SysVinit runlevels
* systemd boot targets

### Terminal commands

* `shutdown`: manage system shutdown.
  * `-t`: seconds to wait.
  * `shutdown +<minutes>`
  * `shutdown HH:MM`
  * `-c`: cancel scheduled shutdowns.
* `shutdown -H` / `halt` / `reboot --halt`: shutdown system without sending signal ACPI for electrical shutdown.
* `shutdown -P` / `poweroff` `halt -p`: shutdown sending ACPI signal.
* `shutdown -r` / `reboot` / `halt --reboot`: reboot system.
* `wall`: sends message to all terminals.
* `mesg y/y`: manage reception of messages.

### SysVinit runlevels

* `runlevel`: current execution level.
* `init` / `telint`: change execution level.
* `update-rc.d`: scripts that get triggered at each level.
  * `update-rc.d <service> enable <level>`
  * Scripts are stored in `/etc/rc<level>.d`

### systemd boot targets

_systemd_'s _"targets"_ are the equivalent of SysVinit's runlevels, as they group units called _"services"_ that we want to run together. Each unit is defined in files such as `<name>.service` and can be stored in different directories such as: `/user/lib/systemd/system`, `/lib/systemd/system` or `/etc/systemd/system`.

You can find more information about units and where are they stored with `man systemd.unit`.

For example, if we want to see what target is run by default:

```
ls /lib/systemd/system default.target -l
```

Or to list all services:

```
ls /lib/systemd/system/*.service
```

And we should use `systemctl` to manage most of _systemd_'s aspect:

### SysVinit compatibility

You can see a linked target for a given SysVinit runlevel:

```
ls -l /lib/systemd/system | grep runlevel
```

### `systemctl`

* `systemctl get-default`: get default target.
* `start/stop/status/etc... unit[.service]` i.e `systemctl restart apache2`
* `isolate unit.target`: change to selected target.
* `list-units [--type=service]`: list loaded units.
* `enable/disable`: active/deactivate an unit.
* `list-dependencies`

## 102.1 Design hard disk layout

Should be able to design a disk partitioning scheme for a Linux system.

### Key knowledge areas

* Allocate filesystems and swap space to separate partitions or disks.
* Tailor the design to the intended use of the system.
* Ensure the `/boot` partition conforms to the hardware architecture requirements for booting.
* Knowledge of basic features of LVM.

### Partial list of used files, terms and utilities

* `/` (root) filesystem
* `/var` filesystem
* `/home` filesystem
* `/boot` filesystem
* EFI System Partition (ESP)
* swap space
* mount points
* partitions

### TOC

* Disk partitioning
* Swap partition
* FHS: Filesystem Hierarchy Standard
* LVM: Logical Volume Manager
* RAID: Redundant Array of Inexpensive/Independent Disks

### Disk partitioning

When installing Linux OS, we need to decide which part of the disk we will use for this purpose.

With Linux, we need at least to partitions: one for the system and other for the swap space

### Swap partitioning

Swap partition serves multiple purposes:

* __Overflow space__ for your RAM. If your RAM fills up completely, any additional applications will run off the swap partition.
* __Prioritization__. Move some itemos from memory to hard drive in order to leave more room in memory for more important items (can configure _"swapiness_").
* __Hibernation__. A swap partition is used as the destination of your memory's contents whenever you tell your system to hibernate.

### Swap space heuristics

* Without hibernation
  * < 2GB RAM: x2
  * 2GB - 5GB RAM: Total RAM + 2gb
  * \> 5GB RAM: depends on system use
* With hibernation
  * RAM + sqrt(RAM)

### FHS: Filesystem Hierarchy Standard

FHS defines the directory structure and directory contents in Linux distributions. It is maintained by the _Linux Foundation_.

In FHS, all files and directories appear under the _root directory_ `/`, even if they are stored on different or virtual devices.

### Directory str8ct8re

* `/`: Primary hierarchy root and _root directory_ of the entire file system hierarchy.
* `/bin`: Essential command binaries that need to be avaiable in single-user mode, for all users (e.g., `cat`, `ls`, `cp`).
* `/boot`: Boot loader files (e.g. kernels, initrd).
* `/dev`: Device files (e.g. `/dev/disk0`, `/dev/sda`, `/dev/tty`).
* `/etc`: Host specific system-wide configuration files. FHS restricts this to static configuration files and may not contain binaries ("Editable Text Configuration" / "Extended Tool Chest").
  * `/etc/opt`: Configuration files for add-on packages that are stored in `/opt`
  * `/etc/sgml`
  * `/etc/X11`
  * `/etc/xml`
* `/home`: User's home directories, containing saved files, personal settings, etc.
* `/lib`: Libraries essential for the binaries in `/bin` and `/sbin`.
* `/lib<qual>` (optional): Alternate format essential libraries.
* `/media`: Mount points for removable media.
* `/mnt`: Temporary mounted filesystems.
* `/opt`: Optional application software packages.
* `/proc`: Virtual filesystem providing process and kernel information as files. Generally, automatically generated and populated by the system, on the fly.
* `/root`: Home directory for the root user.
* `/run`: Run-time variable data, information about the running system since last boot, e.g., currently logged-in users and running daemons.
* `/sbin`: Essential system binaries (e.g. `fsck`, `init`, `route`).
* `/srv`: Site-specific data served by this system, such as data and scripts for web servers, data offered by FTP servers, and repositories for version control systems.
* `/sys`: Contains infromation about devices, drivers, and some kernel features.
* `/tmp`: Directory for temporary files. Often not preserved between system reboots.
* `/usr`: _Secondary hierarchy_ for __read-only user data__, contains the majority of multi-user utilities and applications.
  * `/usr/bin`: Non-essential command binaries (not needed in single-user mode) for all users.
  * `/usr/include`: Standard include files.
  * `/usr/lib` & `/usr/lib<qual>`: Libraries for the binaries in `/usr/bin` and `/usr/sbin`.
  * `/usr/local`: _Tertiary hierarchy_ for local data specific to this host.
  * `/usr/share`: architecture-indpendent (shared) data.
  * `/usr/src`: Source code, e.g., kernel source code with its header files.
  * `/usr/X11R6`: X Windows File System, Version 11, Release 6.
* `/var`: Variable files, files whose content is expected to continually change during normal operation of the system, such as logs, spool files, and temporary e-mail files.
  * `/var/cache`: Application cache data. Such data are locally generated as a result of time-consuming I/O or calculation. Application must be able to regenerate or restore the data.
  * `/var/lib`: State information. Persistent data modified by programs as they run, e.g., databases, packaging system metadata, etc.
  * `/var/lock`: Lock files. Files keeping track of resources currently in use.
  * `/var/log`: Log files.
  * `/var/mail`: Mailbox files (some distros may store this in the deprecated `/var/spool/mail`).
  * `/var/opt`: Variable data from add-on packages.
  * `/var/run`: Run-time variable data. In FHS 3.0, this is replaced by `/run`. A system should either continue to provide a `var/run` directory or a symbolic link from it to `/run` for backwards compatibility.
  * `/var/spool`: Spool for tasks waiting to be processed, e.g., print queues and outgoing mail queue.
    * `/var/spool/mail`: Deprectaed in favor of `/var/mail`.
  *`/var/tmp`: Temporary files to be preserved between reboots.

### Multiuser file systems

Those can be managed in different partitions for performance concerns.

* `/var`
* `/tmp`
* `/home`
* `/usr`: If not going to store many user-specific applications.

### LVM: Logical Volume Manager

> Physical Volume of different disks -> Volume Groups -> Logical Volumes

Device mapper framework that provides logical volume management for the Linux kernel. Most modern Linux distributions are LVM-aware to the point of being able to have their root file systems on a logical volume.

### Uses

* Creating single logical volumes of multiple physical volumes or entire hard disks, allowing for dynamic volume resizing.
  * Volume groups (VGs) can be resized online by absorbing new physical volumes (PVs) or ejecting existing ones.
  * Logical volumes (LVs) can be resized online by concatenating extents onto them or truncating extents from them.
* Managing large hard disk farms by allowing disks to be added and replaced without downtime or service disruption, in combination with hot swapping.
* On small systems, instead of having to estimate at installation time how big a partition might need to be, LVM allows filesystems to be easily resized as needed.
* Performing consistent backups by taking snapshots of the logical volumes.
  * Read only snapshots of LVs (LVM1).
  * Read/write snapshots (LVM2).
* Encrypting multiple physical partitions with one password.
* LVs can be created to include RAID functionality.

### RAID: Redundant Array of Inexpensive/Independent Disks

Data storage virtualization technology that combines multiple physical disk drive components into one or more logical units for the purposes of data redundancy, performance improvement, or both.

Data is distributed across the drives in one of several ways, referred to as RAID levels, depending on the required level of redundancy and performance.

Different schemes / data distribution layouts are named by the word "RAID" followed by a number (e.g. RAID 0). Each scheme, or RAID level, provides a different balance among the key goals: 

* Reliability
* Availability
* Performance
* Capacity

RAID levels greater than RAID 0 provide protection against unrecoverable sector read errors, as well as against failures of whole physical drives.

### RAID 0: Striping

Consists of striping, but no morroring (RAID 1) or parity.

Because striping distributes the content of each file among all drives in the set, the failure of any drive causes the entire RAID 0 volume and all files to be lost, unlike a spanned volumes (disk concatened together, end to beginning, so they appear to be a single large disk) that preserves files on the unfalling drives.

The benefit of RAID 0 is that the throughput of R/W operations to any file is multiplied by the number of drives because, unlike spanned volumes, R/W are done conrurently. The cost is increased vulnerability to drive failures.

## 102.2 Install a boot manager

Should be able to select, install and configure a boot manager.

### Key knowledge areas

* Providing alternative boot locations and backup boot options.
* Install and configure a boot loader such as GRUB legacy.
* Perform basic configuration changes for GRUB 2.
* Interact with the boot loader.

### Partial list of used files, terms and utilities

* `menu.lst`, `grub.cfg` and `grub.conf`
* `grub-install`
* `grub-mkconfig`
* MBR

### TOC

* Startup process & boot loaders
* GRUB: GNU Grand Unified Bootloader
* GRUB2
* Update from GRUB to GRUB2
* GRUB recovery
* Kernel options

### Startup & Boot loaders

BIOS/UEFI delegate control to __boot loader__ which will be responsible for loading the OS.

* __LILO__: Linux Loader, old deprecated loader.
* __GRUB (legacy)__: deprecated in favor of GRUB2.
  * Does not support UEFI.
  * Configuration: `/boot/grub/menu.lst|grub.conf`

### GRUB: GNU Grand Unified Bootloader

GRUB is the reference implementation of the _Free Software Foundation_'s _Multiboot Specification_, which provides a user the choice to boot one of multiple OS installed on a computer or select a specific kernel configuration available on a particular OS's partitions.

GRUB enumerates units and partitions: first disk will be `hd0` and first partition `(hd0,0)`, other partitions will be named similarly.

### Configuration options

* __default__: OS by default.
* __timeout__: seconds to wait for user input.

### OS settings

* __title__: Name to show in menu.
* __root__: Indicates partition that contains the Linux OS (e.g. `root (hd1, 2)`).
* __rootnoverify__: For non-linux OS indicate partiton that contains OS.
* __chainloader__: For non-linux OS, delegate control to other boot loader or `+1` to read `rootnoverify` partiton. 
* __kernel__: Path to kernel file and boot options.
* __initrm__: Path to RAM disk, with options and drivers to boot.

### GRUB2

The main difference is that it supports UEFI firmware. It is the most commonly used boot loader for all Linux distributions.

It inherits the GRUB's nomenclature but partitions start at `1`, and some other differents as `rootnoverify` replaced by `root`.

GRUB presents a menu where the user can choose from operating systems (OS) found by grub-install. GRUB can be configured to automatically load a specified OS after a user-defined timeout. If the timeout is set to zero seconds, pressing and holding `⇧ Shift` while the computer is booting makes it possible to access the boot menu.

### Configuration

Configuration menu __cannot be modified manually__. Options are customized in `/etc/default/grub` and other data are obtained by scripts in `/etc/grub.d`.

To generate `/boot/grub/grub.cfg`, you execute `update-grub` or `grub-mkconfig`, and to install grub2 `grub-install`.

### Update from GRUB to GRUB2

```
apt-get install grub2
nano /etc/default/grub
update-grub2
upgrade-from-grub-legacy
```

### GRUB Recovery

You can start from an installation disk, and from `Advanced Options` you can enter `Rescue mode` and enter to partition's interpeter that you had previously installed linux.

```
update-grub2
grub-install /dev/sda
```

### Kernel Options

```
nano /etc/default/grub
update-grub2
```

* __quiet__: avoid startup messages.
* __debug__: see debug messages.
* __init__: replace startup program instead of `/sbin/init` (e.g. `init=/bin/bash`).
* __single__: execute single-user mode.
* __root__: define partition that stored root OS.
* __RO__/__RW__: read-only.
* __mem__: forces RAM amount (e.g. `mem=1024M`).
