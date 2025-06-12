---
title: "Build your own Installer"
date: 2021-10-29T15:42:42+01:00
draft: false
icon: "fa-solid fa-hands"
download-base: "/"
os: "diy"
os_weight: 40
machine: "generic|RaspberryPi4|ARM64EFI"
arch: "x86_64|aarch64"
rpm_version: "5.0.9"
rpm_release: "0"
installer_patch: ""
---

All our "Built on openSUSE" installers are made using the [Rockstor Installer Recipe](https://github.com/rockstor/rockstor-installer).
This in-turn uses the excellent [Kiwi-ng](https://github.com/OSInside/kiwi) open source image and appliance builder from openSUSE.
[Kiwi-ng's docs](https://osinside.github.io/kiwi/).

You can also create your own custom profile tailored to your specific needs.
Please see our [Custom Solutions]({{< relref customizable-btrfs-nas-storage-platform.md >}}) for context.

All upstream updates, at installer build/re-build date/time, are pre-applied to the resulting image.

***We welcome profile contributions where our existing profiles are insufficient.*** 
