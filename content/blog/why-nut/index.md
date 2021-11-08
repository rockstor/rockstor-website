---
title: "Why Nut"
date: 2015-11-10T15:30:25Z
draft: false
author: Philip Guyton
aliases:
    - /blog/dogfooding/why-nut/index.html
resources:
- name: header  # Don't change this name: used in list layout.
  alt: ups examples
  src: ups-examples-1024x576.jpg
- alt: ups examples
  src: ups-examples-1024x576.jpg
- alt: series of serial adapters
  src: serial-adaptation-1024x575.jpg
- alt: electrical mouse problem
  src: electrical-mouse-problem-1024x576.jpg
- alt: walNUT gnome extension
  src: walNUT_gnome_extension.jpg
---

Expectation doesn't always match actuality, which is a shame, but sometimes we can do something about it.
This is a tiny tale of my attempt to do just that.
<!--more-->

{{< figure src="./why-nut/ups-examples-1024x576.jpg" width=100% alt="ups examples" >}}

---
Early in 2015 I was on the lookout for a [linux](https://en.wikipedia.org/wiki/Linux) based Network Attached Storage (NAS) system that had the more enterprise goodness I had encountered with my ventures into [ZFS](https://en.wikipedia.org/wiki/ZFS) via [FreeNAS](http://www.freenas.org/)
i.e. Copy on Write (CoW), data checksums, snapshots etc., and happened across [Rockstor](https://rockstor.com/); but at the time it had no graphical Uninterruptible Power Supply (UPS) configuration.
This for me was a show stopper (story to follow), my expectation was to adopt my dream NAS setup that ran on my favourite Operating System (OS) and to have an all Linux setup once again.
Actuality was falling short.

Sure I was impressed with FreeNAS but I'm a Linux guy and having been an all Linux setup for 15 years at least,
it grated to be using [NanoBSD](https://www.freebsd.org/doc/en/articles/nanobsd) for my NAS.
Nothing against FreeNAS but my mainstay OS of choice was set and I had grown very familiar with it;
the BSD's for all their splendour were just not my cup of tea and it sat uneasy that my darling OS was just not serving me in every way I wanted.
It had been years since I'd looked at Linux NAS ditributions so surely something had happened.
It was at this point that I first came across Rockstor.
This thing was neat, focused, to the point, and most encouragingly developed completely in the open.
Sure it was still quite young at less than two and a half years but the pace of development was fast.
That's great I thought, if it has what I need then marvellous but alas it was short of one key feature.
It had no graphical way to configure [Network UPS Tools](http://www.networkupstools.org/index.html) (NUT), a UPS tools system, and for me this was just not the ticket.
Given that Rockstor ~~is~~ was essentially a full [CentOS](https://www.centos.org/) (EDIT: now [openSUSE](https://www.opensuse.org/)) with a WebUI bolted on to deal with the [btrfs](https://btrfs.wiki.kernel.org/index.php/Main_Page) / NAS / sharing stuff
I knew I could simply do a text based NUT config but that wasn't what I wanted.
That wasn't an appliance.
I had already spent many years doing everything with my teeth even down to the early days of mode lines in [X windows](http://www.x.org/wiki/) and reserving memory just to get 3D going,
and regular kernel recompilations or [CUPS](https://en.wikipedia.org/wiki/CUPS) recompilations just to be able to print.
My Linux should be better than that, it should by now be for the people; all the people.
With all the goodness of a modern file system.

So I wondered on by.
But the whole Rockstor dabble had left a lasting impression and I just couldn't shake the fact that I was just not happy running a NanoBSD based system when my passions and interests were Linux based.
It also greatly excited me that I might once again become an all Linux setup.
I enjoy the Linux ethos and I believe the nature of the licence to be key: i.e. Apple’s advancements in BSD that no one else has.
Alas; sometimes expectation just doesn't match actuality.

But hold on I thought, I can't let a little thing like a missing feature stand in my way.
I began making tentative inroads into [Rockstor's community forum](https://forum.rockstor.com/) and the [GitHub hosted code](https://github.com/rockstor/rockstor-core) to see what I might do to make a difference.
There were some unusual elements to this NAS distro, they had obviously made significant efforts towards usability, you know where things make sense due to design; an all too sparse quality in many OSs.
I slowly and surely became convinced that this was an OS NAS OS (open source NAS operating system) of the future, in the making.
And I wanted to be part of that future.

Oh and what [Brett said](http://45drives.blogspot.co.uk/2015/09/why-i-love-rockstor-on-our-storinators.html#more).

Sometimes one just has to adapt to a situation and sometimes one can adapt the situation.

{{< figure src="./why-nut/serial-adaptation-1024x575.jpg" width="648" height="364" alt="series of serial adapters" >}}

Adaptation by adapter. Not all FT232R’s are equal; a null modem wired usb to serial adapter adapted for UPS testing. Sorted.

## Part of the future
At that time the forum was run on something decidedly inferior to [Discourse](https://www.discourse.org/)and wouldn't even render in my browser of choice, this wasn't good.
So I dove into the git repository and browsed the issues and pull requests to try and gain a deeper understanding.
In my meandering I saw one or two tiny fixes I could make and on a whim started submitting the smallest of pull requests.
Whilst exploring the feature set further I received a friendly error message that something had gone wrong.
Nicely caught and no horrible crashes just a neat dialog encouraging me to send an automatically prepared zip of logs to the developers.
Elegant I thought.
Not just a long wait in the nothingness of an unresponsive system but true assistance and guidance.
I was further impressed.
So I downloaded the log zip and not wanting to bother the developers with my silly problem I took a peak.
What I saw was something crafted, full on [Python](https://www.python.org/) with exceptions caught everywhere,
not just another [PHP](https://en.wikipedia.org/wiki/PHP) monster but a proper structured entity with objects and fancy ways and means.
Anyway, the logs pretty much pinpointed the problem but I just wasn't familiar enough with the code to tackle this myself so in the interests of living up to my ideals I posted an issue.

The response to my issue was surprisingly fast and entirely jovial; I had (in internet terms) met [Suman](http://rockstor.com/about-us.html), the project lead.
A fix was committed and in no time at all my silly little issue was sorted, and this was good.
The joys of a rapid development cycle.

Soon thereafter the forum software was thankfully switched to the most excellent open source discourse and was becoming alive with the growing interest in this newfangled btrfs NAS solution.
I was, perhaps unwisely, awarded the privilege of forum maintainer; a pretty friendly place so no worries there.
By then I had also submitted some doc tweaks and additions.
To my surprise I found the [docs](https://rockstor.com/docs/) to be programmatically generated from .rst files,
a mark up format know as [reStructeredText](https://en.wikipedia.org/wiki/ReStructuredText) that through the magic of [Sphinx](http://sphinx-doc.org/) ends up as html for the Rockstor home page docs section.
This was just getting better and better, and I had started to make a difference.
At about the same time I ventured an email declaring my interest in adding NUT and was pleasantly surprised by the encouraging return.
They had no plans to implement this feature "just yet" but they were all to happy to help in whatever way they could.
So why NUT; or maybe why not NUT.

## Why not NUT
So why not NUT, why bother, well indeed; in the context of no doubt well meaning mice this is a question that answers itself.
But stories are nice so here goes.

Over time where I live and work the electric had been a little iffy, the occasional trip out but nothing too serious.
I had as a matter of course implemented a number of UPS’s and hand configured NUT to deal with these little outages but more was to come.

One morning I awoke to a calmness, this can’t be bad I thought, but there was a down side.
The entire electric had failed and this time there was no just flipping it back on and going about my business no no.
This time it was serious.
It turned out that we could no longer make any sockets live; the [Residual Current Device](https://en.wikipedia.org/wiki/Residual-current_device) (RCD) refusing to enact our expectation.
An investigation was in order.

#### The investigation
Most people who have dealings with computers have had mouse problems at one time or another, these days the problems tend not to be physical but electrical; given the prevalence of optical mice.
It turned out that my electrical problem was both physical and mouse related.

{{< figure src="./why-nut/electrical-mouse-problem-1024x576.jpg"  width="648" height="365" alt="electrical mouse problem" >}}

The mouse problem diagnosed; definitely both physical and electrical and behind a drywall at the back of a cupboard.
Inconvenience incarnate.
So without ripping apart my whole (rented) accommodation I can only assume that other as yet undiscovered gems such as the above are lying in wait.
What's in your walls?

After many hours of diagnostics and much frustration I had found at least one reason for our previously flaky and now critical electric situation.
Needless to say my NUT interest grew and I began as a matter of course to make all systems aware of their pending doom; or at least when it might be a good idea to shut down.
NUT, due to it’s network nature, is a perfect fit.

To cut a long story short I ended up submitting (on my 47th birthday) my first non trivial pull request to Rockstor core.
A fortnight of advice reviews and tweaks later and Rockstor now has graphical NUT configuration ~~(in beta)~~.
I for one am chuffed.
And yes wouldn't it be great to have a nice UPS data page or a whizzy additional widget on Rockstor's dashboard but until that time,
successive approximation and development in the open and all, I offer up some "desktop" shiny.

## Some shiny
Given no fancy technology is complete without fancy telemetry; I present [walNUT](https://github.com/zykh/walNUT).

{{< figure src="./why-nut/walNUT_gnome_extension.jpg" width="668" height="376" alt="walNUT gnome extension" >}}

walNUT the [Gnome](https://www.gnome.org/) Shell Extension to monitor one’s UPS, thanks [Daniele](https://github.com/zykh).

And for those of a [KDE](https://www.kde.org/) persuasion there is [KNutClient](https://sites.google.com/a/prynych.cz/knutclient/home), thanks [Daniel](https://sites.google.com/a/prynych.cz/knutclient/home/contact-us).

Note the similarity in the names; funny that.
[Graphical NUT clients](http://www.networkupstools.org/projects.html#_graphical_desktop_clients) are also available for other popular platforms.

**What are these things but what we make them.**