---
title: "Stringer"
Description: "Portable Wordprocessor and Terminal Hardware"
date: 2023-05-29T18:31:10-04:00
draft: false
---

# Stringer Word Processor
## A low-tech digital word processing unit

Stringer is a bespoke small form factor lo-tech computer purpose built for offline pros drafting. Stringer refers to the process of stringing words, sentences and paragraphs together.

### Overview

I am interested in creating dedicated devices, machines that are assembled and configured for a single task. While creating a digital typewriter like Stringer may not be a new idea, I am confident in my ability to conduct thorough research on the topic and arrive at unique ideas and thoughtful design decisions. I have delved into the history of typewriters, digital word processors, as well as many obscure word processing tools. Through this discovery process, I have gained an appreciation for various software and hardware components that are often overlooked.

### Problems 

1. Common computers are sophisticated multitasking devices that threaten to distract us.
2. Complex and proprietary systems are difficult to repair and/or maintain, resulting in huge amounts of E-Waste.
3. Most modern electronic devices are dependent on online connectivity and accounts in order to simply operate.
4. Other writing devices do not provide modern macros and scripting capability.
5. It is nice to have a dedicated device that just works without changing for years.
6. It is nice to use simple configuration files to define functions, shortcuts and macros rather than a plethora of menus.

### Stringer Functional build requirements

* A lower power draw Single Board Computer (SBC).
* A lower power draw display (E-ink or Small LCD).
* Uninteruptable power supply (UPS).
* Capability of running, charging and transferring data through a single cable.
* The unit will be able to umelate a keyboard and output a files raw text by typing it out much like an alphasmart.
* The unit will have multiple disks in mirrored raid configuring.
* The unit will be ruggedized to endure long term use and neglect.

### Stringer Aesthetic build requirements

* Artisitc PCB's throughout (Edition Based)
* Sandwiched PCB construction with spacers, framed like a window. PCB slots into wooden frame.
* Ortholinear keyboard with extensions on either side for many macro keys.
* Grid of small tactile switches and LED's for macros (Saving, Battery Check, Reboot, Config files).
* Custom stringer config for all software.
* Easy deconstruction for repair / cleaning.
* Fully Open Schematics, Build notes, Scripts, Software configs.

### Stringer Software requirements

* Barebones operating system with power usage optimizations.
* Minimal Desktop or terminal environment.
* Minimal Text Editor.
* Everything is a config file.
* Snaptshotting and/or copying to redundant storage like a cron job.

### Software Installer / ISO requirements

* A bespoke OS image that can run from an SD card.
* All config files are bundled within the ISO.
* A bespoke splash screen with user creation process.

### Stringer Support Requirements

* Dedicated website (Hugo).
* Hosted Stringer image on site (ISO files with releases).
* Excellent documentation (FreeBSD like).
* Many illustrations and renderings (Shareable, linkeable promotional materials).
* Printed manual that is a mirror of the online documentation.
* Printable replacement parts.

---

# Candidate Components:
### Computer

- [Olimx OLinuXino Lime2 SBC](https://www.olimex.com/Products/OLinuXino/A20/A20-OLinuXino-LIME2/open-source-hardware) 
- [Second SD Card Daughter board](https://www.olimex.com/Products/OLinuXino/A20/Lime2-SD/open-source-hardware)

### Battery

- [6600MAH Li-PO battery with JST connector](https://www.olimex.com/Products/Power/Lipo-battery/BATTERY-LIPO6600mAh/)

### Keyboard

- Custom PCB (TBD)
- Khali Choc v1 Switches x 60
- Custom moulded keycaps based on MBK Choc Low Profile x 60
- 1N4148 Diode x 60
- Arduino Pro Micro 

# Candidate Software:

### Operating System (OS): Alpine Linux

### Window Manager (WM): BSPWM

### Text Editor: VIM 9 with plugins: GOYO, LimeLight, VIM-PENCIL, Proselint, Ale. 

### Multiplexor / Session Handler: TMUX with plugins: TPM, Resurrect.

### Hardware Macro System: QMK 

---

# Outside links to Inspiration / Comparables:

* [Low Budget Word Processor Taredown](https://hackaday.com/2020/06/09/teardown-the-writer-word-processor/)
* [Fully Realized Printed Unit](https://yarh.io/thebrick.html)
* [Long Slim Formfactor Machine](https://github.com/penk/penkesu)
* [Highly aesthetic bespoke machines](https://www.lovehulten.com/)
* [Commercial Successful Digital Typewriter](https://getfreewrite.com/products/freewrite-smart-typewriter-3rd-gen)


