---
title: "Rockstor Git Gource – project visualization"
date: 2017-11-07T13:44:41Z
draft: false
author: Philip Guyton
aliases:
    - /blog/btrfs-nas/rockstor-git-gource-visualization/index.html
# Each blog post is a Hugo leaf page bundle (index.md).
# Blog page bundles are blog section members (page type "blog") (_index.md).
# This makes the top level blog section content (_index.md) a branch bundle.
# Image resources placed in same folder as blog index.md (leaf page bundle).
resources:
- name: header  # Don't change this name: used in list layout.
  alt: gource git snapshot showing many names June 2017
  src: june2017-gource-snapshot-1024x576.png
---

## Gource is Git shiny.

[Gource](http://gource.io/) is an open source GPLv3 licensed OpenGL visualiser of Git/SVN/Mecurial, and Bazaar repositories over time.
<!--more-->

{{< figure class="img-responsive" src="./rockstor-git-gource-visualization/june2017-gource-snapshot-1024x576.png" width=100% alt="gource git snapshot showing many names June 2017" >}}

---
From Wikipedia’s “[A picture is worth a thousand words](https://en.wikipedia.org/wiki/A_picture_is_worth_a_thousand_words)”:

The actual [Chinese](https://en.wikipedia.org/wiki/Chinese_language) expression *"Hearing something a hundred times isn't better than seeing it once"*
[百](https://en.wiktionary.org/wiki/%E7%99%BE)
[闻](https://en.wiktionary.org/wiki/%E9%97%BB)
[不](https://en.wiktionary.org/wiki/%E4%B8%8D)
[如](https://en.wiktionary.org/wiki/%E5%A6%82)
[一](https://en.wiktionary.org/wiki/%E4%B8%80)
[见](https://en.wiktionary.org/wiki/%E8%A7%81),
[p](https://en.wikipedia.org/wiki/Pinyin) **bǎi wén bù rú yī jiàn**
is sometimes introduced as an equivalent, as [Watts](https://en.wikipedia.org/wiki/Alan_Watts)'s *"One showing is worth a hundred sayings"*.
[[6]](href="https://en.wikipedia.org/wiki/A_picture_is_worth_a_thousand_words#cite_note-6).
This was published as early as 1966 discussing persuasion and selling in a book on engineering design.
[[7]](href="https://en.wikipedia.org/wiki/A_picture_is_worth_a_thousand_words#cite_note-7).

**Rockstor's 5 git repositories visualised in just over 1.5 minutes:**

See YouTube [Gource visualization of rockstor-core](https://www.youtube.com/watch?v=NSSYp8q1peo)

The essence of Gource’s use is to point it at a copy of one’s repository.
The wrinkle here is that Rockstor consists of multiple repositories:

- rockstor-doc - our docs in their original restructured text format.
- rockstor-core - the main code repository.
- rockon-registry - our docker based ‘rock-on’ plugins repo.
- rockstor-iso - code / artifacts concerning the creation of our stable release iso images.
- rockstor-jslibs - the collection of js libraries we use to do what js does best.

But fear not as the now 29 [Edit now 34] strong developers of Gource have us covered in their appropriately named:
[Visualizing-Multiple-Repositories](https://github.com/acaudwell/Gource/wiki/Visualizing-Multiple-Repositories).

**"Sometimes it may be interesting to show the history of multiple projects in the same Gource animation."**

Here we re-tell the above but for Rockstor's repositories.
The hope is that this ‘telling’ might aid other multi-repo projects and save us all some time; at least on mass.

#### Building Gource
As of 8th September 2017 v0.47 was released which is the version I used.
Be sure to visit their [releases](https://github.com/acaudwell/Gource/releases)</a> page to check for newer releases.
As always please favour the projects own [INSTALL](https://github.com/acaudwell/Gource/blob/master/INSTALL) doc over what I state here.
But for completeness I’ll indicate how it worked for me:

Using a Fedora26 desktop:

```bash
sudo dnf install git freetype-devel pcre-devel glew-devel SDL2-devel SDL2_image-devel boost-filesystem boost-devel glm-devel
mkdir ~/Downloads/gource
cd ~/Downloads/gource
wget https://github.com/acaudwell/Gource/releases/download/gource-0.47/gource-0.47.tar.gz
tar xvf gource-0.47.tar.gz
cd ~/Downloads/gource/gource-0.47
./configure
make
```

We refrain from ‘make install’ to keep all our gource activities confined to our Downloads dir. (snap / flatpak suggestions anyone?)

Now we jump up a directory and grab a local copy of Rockstor’s repos:

```bash
cd ~/Downloads/gource/
git clone https://github.com/rockstor/rockstor-core.git
git clone https://github.com/rockstor/rockstor-doc.git
git clone https://github.com/rockstor/rockon-registry.git
git clone https://github.com/rockstor/rockstor-jslibs.git
git clone https://github.com/rockstor/rockstor-iso.git
```

then we resource Gource’s ability to create a custom-log of activity spanning all the above repos. For this we jump back into our gource build directory:

```bash
cd ~/Downloads/gource/gource-0.47
```

and point the binary at each of the rockstor repos in turn with switches requesting our needed custom logs.

```bash
./gource --output-custom-log ../doc-log.txt ../rockstor-doc/
./gource --output-custom-log ../core-log.txt ../rockstor-core/
./gource --output-custom-log ../rockon-log.txt ../rockon-registry/
./gource --output-custom-log ../iso-log.txt ../rockstor-iso/
./gource --output-custom-log ../jslibs-log.txt ../rockstor-jslibs/
```

Then back up to our new logs:

```bash
cd ~/Downloads/gource/
```

Next we make our repos more distinct by putting them on separate branches via multiple stream edits (sed):

``` bash
sed -i -r "s#(.+)\|#\1|/doc-repo#" doc-log.txt
sed -i -r "s#(.+)\|#\1|/core-repo#" core-log.txt
sed -i -r "s#(.+)\|#\1|/rockon-repo#" rockon-log.txt
sed -i -r "s#(.+)\|#\1|/iso-repo#" iso-log.txt
sed -i -r "s#(.+)\|#\1|/jslibs-repo#" jslibs-log.txt
```

Now we combine our custom activity logs in a single “all-rockstor-repos-log.txt” thus:

```bash
cat doc-log.txt core-log.txt rockon-log.txt iso-log.txt jslibs-log.txt | sort -n &gt; all-rockstor-repos-log.txt
```

And finally, at least for now, we can move back to our binary dir:

```bash
<code>cd ~/Downloads/gource/gource-0.47/
```

#### Gource Plays Rockstor Repos

**Rockstor dev at 20 days a second = 1m 37s:**

(Less than fair as major contributions / contributors flash by but serves as a quick test run.)


```bash
./gource -1280x720 --seconds-per-day 0.05 --highlight-users --highlight-colour E76545 --hide filenames --hide-root --multi-sampling ../all-rockstor-repos-log.txt
```

And if you liked that, try the slightly more sane speed variant of:

**Rockstor dev at 5 days a second = 5m 43s:**


```bash
./gource -1280x720 --seconds-per-day 0.2 --highlight-users --highlight-colour E76545 --hide filenames --hide-root --multi-sampling ../all-rockstor-repos-log.txt
```

Note the following abstract of the interactive controls:

- (TAB) key to switch user highlight
- (Space bar) pause / resume the animation
- (V) center camera on above user (if selected) - bit much on the brain
- (F12) Screenshot
- (Alt+Enter) Fullscreen toggle - a winner this one
- (+-) Adjust simulation speed
- (ESC) Quit

There’s also a nice selection of mouse interactions such as jumping to any time point; although this does reset the graph.
While paused one can inspect the details of individual files and users, and dragging with the left mouse button manually controls the camera.
Centre button toggles tracking / entire tree view.

#### Building the Bling Vid

To capture the raw video we use Gource’s “-o” switch.

**Entire dev history in 1.5m (earlier video):**


```bash
./gource -1280x720 --seconds-per-day 0.05 --highlight-users --highlight-colour E76545 --hide filenames --hide-root --multi-sampling ../all-rockstor-repos-log.txt -o ../rockstor-dev.ppm
```

We then encode to x264 via ffmpeg from Negativo17’s multimedia repo:
[https://negativo17.org/handbrake/][https://negativo17.org/handbrake/] ([Elrepo](https://elrepo.org/tiki/tiki-index.php) dependency) Thanks.

```bash
sudo dnf install ffmpeg
```

```bash
ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i ../rockstor-dev.ppm -vcodec libx264 -preset medium -pix_fmt yuv420p -crf 20 -threads 0 -bf 0 ../rockstor-dev.mkv
```

And 16.2 GB becomes 33 MB.

**Entire dev history in just under 6 minutes (slightly less manic):**

See YouTube [Gource visualization of rockstor-core (long)](https://www.youtube.com/watch?v=sBFpeEhPpk8)

```bash
./gource -1280x720 --seconds-per-day 0.2 --highlight-users --highlight-colour E76545 --hide filenames --hide-root --multi-sampling ../all-rockstor-repos-log.txt -o ../rockstor-dev-long.ppm
```


```bash
ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i ../rockstor-dev-long.ppm -vcodec libx264 -preset medium -pix_fmt yuv420p -crf 20 -threads 0 -bf 0 ../rockstor-dev-long.mkv
```

57 GB via a similar ffmpeg command (differing file names) becomes 60 MB: bargain.

**And finally the last 90 days at the rather more sedate 1 second/day = 1m 31s:**

```bash
./gource -1280x720 --seconds-per-day 1 --start-date $(date -I --date='-90 days') --highlight-users --highlight-colour E76545 --hide filenames --hide-root --multi-sampling ../all-rockstor-repos-log.txt -o ../rockstor-dev-last-90days.ppm
```

```bash
ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i ../rockstor-dev-last-90days.ppm -vcodec libx264 -preset medium -pix_fmt yuv420p -crf 20 -threads 0 -bf 0 ../rockstor-dev-last-90days.mkv
```

Where 15 GB via ffmpeg becomes 9 MB.

Note that as with the mouse 'time jumps' in the interactive mode covered earlier, using the "--start-date" option, as we have just done, results in no previous activity being displayed.
That is, only files changed after the given date, and their respective repositories, will appear in the resulting Gource graph.

And thus we have our thousand words.

