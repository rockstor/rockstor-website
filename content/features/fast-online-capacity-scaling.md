---
title: "Fast Online/Live Capacity Scaling - Larger or Smaller"
date: 2021-10-15T15:45:40+01:00
draft: false
icon: "fa fa-arrows-v"
doclink: "/docs/interface/storage/pools-btrfs.html#pool-resizing"
---

Disks can be added or removed to grow or shrink storage pools while simultaneously serving clients.
<!--more-->
Directly from the Web-UI via step-by-step wizards.
Similarly, Pool redundancy profiles and Share capacities can be updated without service interruption.
Shares and Pools can be thin provisioned and can grow along with capacity need.
BTRFS, our linux kernel based filesystem, supports practically unlimited capacity (16 EiB / Pool/Volume).
