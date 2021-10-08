---
title: "Rockstor to Rockstor Replication"
date: 2021-10-15T17:04:55+01:00
draft: false
icon: "fa fa-refresh"
doclink: "/docs/interface/storage/share_replication.html"
---

Using Rockstor's asynchronous replication feature, users can configure Shares to be replicated to another Rockstor instance on a schedule.
Replication uses the **BTRFS send/receive feature** to efficiently transfer only the on-disk block changes.

