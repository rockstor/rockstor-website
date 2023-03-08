---
title: "Install on Vanilla openSUSE/SuSE SLES"
date: 2021-10-29T18:06:54+01:00
draft: false
icon: "fa-solid fa-hands"
download-base: "/"
os: "rpm"
os_weight: 40
machine: "generic"
arch: "x86_64"
rpm_version: "4.5.8"
rpm_release: "0"
installer_patch: ""
---


Our installer profiles, and consequently our pre-build installers, deviate only a little from openSUSE's JeOS appliance profiles.

It is possible, **but not recommended or supported**, to add the relevant Rockstor repositories to a **dedicated** vanilla openSUSE / SuSE SLES non transactional server install.
Assuming the base OS version is already found within our [Rockstor 4 Installer Recipe](https://github.com/rockstor/rockstor-installer).
And in the case of SLES, is at least version 15.4 when the upstream binary compatibility between openSUSE Leap & SuSE SLES matured.  

### **For advanced users only**
 
*This install method is predominantly for developers or advanced users and will likely require additional maintenance.
It may also serve as an option where a SLES base is required.*
**Please note our undesirable disabling of apparmor.** We hope to resolve this partial failure in due time.

### Relevant commands (assuming a 15.4 base version):

---

systemctl disable apparmor

zypper install \--no-recommends NetworkManager

systemctl disable wicked

systemctl enable NetworkManager

systemctl start NetworkManager

(**multiarch**) zypper \--non-interactive addrepo \--refresh -p105 https://download.opensuse.org/repositories/home:/rockstor/15.4/ home_rockstor

(**multiarch**) zypper \--non-interactive addrepo \--refresh -p97 https://download.opensuse.org/repositories/home:/rockstor:/branches:/Base:/System/15.4/  home_rockstor_branches_Base_System

rpm \--import https://raw.githubusercontent.com/rockstor/rockstor-core/master/conf/ROCKSTOR-GPG-KEY

(**multiarch**) zypper addrepo -f http://updates.rockstor.com:8999/rockstor-testing/leap/15.4/ Rockstor-Testing

zypper \--non-interactive \--gpg-auto-import-keys refresh

zypper in \--no-recommends rockstor-{{< param rpm_version >}}-{{< param rpm_release >}}

systemctl enable \--now rockstor-bootstrap

**Please note that Rockstor is not yet Multi-path controller compatible.**

**As always GitHub Pull Requests are Welcome.**






 