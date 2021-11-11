---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
author: Your-name-here
# Each blog post is a Hugo leaf page bundle (index.md).
# Blog page bundles are blog section members (page type "blog") (_index.md).
# This makes the top level blog section content (_index.md) a branch bundle.
# Image resources placed in same folder as blog index.md (leaf page bundle).
resources:
- name: header  # Don't change this name: used in list layout.
  alt: img alt text
  src: header-image.jpg
---