---
layout: post
title: "Writing Images to Flash Drives"
date: 2012-08-03 22:36
comments: true
categories: Fedora
---

It seems odd that there are no obvious ways to write a disk image to a USB
flash drive from a Linux system, when there are so many options for burning
images to a CD.  I often find myself wanting to run a "Live CD" and using a
flash drive instead is both faster and less wasteful.

<!-- more -->

So we have to resort to low-level tools like `dd`:

    $ sudo dd if=Fedora-17-x86_64-Live-Desktop.iso of=/dev/sdh bs=8M conv=fsync

This is assuming your USB flash drive is the `/dev/sdh` device; you can
find out with `dmesg` or a tool like GNOME's "Disks" utility.

So this works, but there's not a whole lot of feedback.  The `dd` program
is like that.  The man page suggests we can get it to print some statistics
by sending the USR1 signal to it.  Hokay.  Need to open a new terminal for
this!

    $ pkill -USR1 ^dd$

Cool!  But wouldn't it be nice if `dd` had a progress bar or somesuch,
without requiring a new terminal just to get some feedback?  Enter `pv`.

    $ sudo yum install pv
    $ pv Fedora-17-x86_64-Live-Desktop.iso | sudo dd of=/dev/sdh bs=8M conv=fsync

Enjoy!
