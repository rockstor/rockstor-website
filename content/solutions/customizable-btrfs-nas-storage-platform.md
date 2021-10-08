---
title: "Customizable Btrfs NAS Storage Platform"
date: 2021-10-08T18:55:23+01:00
draft: false
---
---
Rockstor as a Cloud and Storage platform enables hackers, makers/re-distributors, and DIYers to build completely custom solutions.
Storage is an essential part of most software and hardware projects
– be it an embedded project or a web application, but options for a robust storage layer with complete control are limited.


### With **Rockstor as a platform**, you can:

- Build you own custom installer via our open source [Installer Recipe](https://github.com/rockstor/rockstor-installer).
- Build your own dependable storage platform with ease.
- Run on almost any hardware or hypervisor.
- Use our APIs to provision resources on demand.
- Take full advantage of BTRFS and customize it to your needs.
- Join our [community forum](https://forum.rockstor.com/) with strong hacker presence and benefit from knowledge sharing.

<!--more-->

Rockstor as a Cloud and Storage platform can be leveraged by hackers, makers/re-distributors, and DIYers in their projects to craft custom solutions.
Public cloud solutions are great, but when they are not appropriate, users end up having to build and maintain a NAS setup themselves.
With Rockstor, users can setup not only a traditional NAS, but a dependable storage/service platform with ease.
It's API enables users to provision resources on demand, take advantage of BTRFS and customize to their needs.
As a Linux operating system "Built on openSUSE", Rockstor can be tweaked and tuned to your needs.
Our community has a strong hacker presence where information can be shares freely to benefit us all.
And where anyone can contribute to help form our future features set.

{{< ps phrase="Custom Hardware" >}}
## Problem
You have built or supply custom hardware that need out-of-tree or extremely modern hardware compatibility.
Be it proprietary drivers, i.e. for Cuda compute, or custom network and/or display controllers. 

## Solution
We have you covered.
As we are now "Built on openSUSE" we already have excellent hardware compatibility with openSUSE being one of the longest running ARM compatible distributions.
But they still have have their LTS kernel SLES binary compatibility requirements you say and these don't meet our hardware/custom needs.
Fine, so follow the [excellent openSUSE docs](https://doc.opensuse.org/documentation/leap/reference/html/book-reference/cha-tuning-multikernel.html#sec-tuning-multikernel-latest)
on installing your preferred/required kernel and/or drivers and be ready to roll.
As we actively track the openSUSE Leap releases, since 15.0, we welcome any bug reports from such 'future' kernels that serve as our head-up on what is to come.
In time we hope to again offer a Tumbelweed base, but we must first fix our Python 2 dependencies.
Watch [this space](https://github.com/rockstor/rockstor-core/issues/2254) on that front.
{{< /ps >}}

{{< ps phrase="Custom Installer" >}}
## Problem
I/We need more than what Rocksor is; an appliance approach is fine for the majority of cases but not for us.

## Solution
If you can do it on an up-to-date openSUSE Leap you can do it on Rockstor.
We are a very lightly modified "Built on openSUSE" endeavour, comprising progressively fewer base OS modification.
But I need complete control of even the installer, or else I/our clients/users have way too many hoops to jump through.
Or we can't even get off the ground; i.e. custom interfaces/controllers/configurations.
Again, fine.
Build you own [kiwi-ng](https://github.com/OSInside/kiwi) profile: that's what we did [Rockstor 4 Installer Recipe](https://github.com/rockstor/rockstor-installer).
It's also what [Traverse Technologies](https://traverse.com.au/) did for their cutting edge [Ten64](https://www.crowdsupply.com/traverse-technologies/ten64) ARM64 server platform.
Their co-operation and profile contributions have in turn lead us to now officially supplying these otherwise custom builds which are also [Embedded Boot](https://github.com/ARM-software/ebbr) or [Server boot](https://github.com/ARM-software/sbsa-acs) compatible.
We have a win win.
The open source GNU way. 
And given openSUSE/SuSE use the exact same technology for their own installers and appliance images we are in good company.
See the excellent [Kiwi-ng docs](https://osinside.github.io/kiwi/) for the possibilities.
{{< /ps >}}

{{< ps phrase="Custom Config" >}}
## Problem
You have services and pre-configuration needs that are not currently met by our default.
You've invested ages and/or euros in establishing exactly what you/your clients/offices/etc need.
How do you setup you bare metal recovery to be up-and-running as quickly as possible. 

## Solution
Simple, incorporate your additional core packages and pre-edited config directly into your own Custom Installer profile.
The [kiwi-ng](https://github.com/OSInside/kiwi) installer technology also allows for embedding your own custom configuration files.
You can be up-and-running with your (not our) default configuration right from the minute the installer finishes.
You don't even need to re-boot post install, but it's still a good idea :).
Oh and did you know that whenever you build your own installer, it auto incorporates all the latest upstream (read openSUSE) updates; rolled right into your final image.
This in turn can save countless hours across you systems / spare-time / offices / clients.
And come the day a new critical bug is fixed, it gets rolled right into your next installer build.  
{{< /ps >}}