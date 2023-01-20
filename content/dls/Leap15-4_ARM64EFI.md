---
title: "Leap15 4_ARM64EFI"
date: 2023-01-20T17:21:01+01:00
draft: false
icon: "fa fa-linux"
download-base: "/"
os: "Leap15.4"
os_weight: 40
machine: "ARM64EFI"
arch: "aarch64"
rpm_version: "4.5.5"
rpm_release: "0"
installer_patch: ""
---

[Stable Release Candidate status](https://forum.rockstor.com/t/v4-5-testing-channel-changelog/8546/6)

**Note:** *Btrfs parity raid levels (5&6) are read-only by default.*

Awaiting Custom Ten64 drivers (may not be required any longer).
Consider our [Installing the Stable Kernel Backport](https://rockstor.com/docs/howtos/stable_kernel_backport.html)
to enable parity raid read-write access and for improved hardware compatibility.
**NOTE: backports how-to needs modifying for 15.4**