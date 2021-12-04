---

[//]: # (@formatter:off)
layout: page
title: MacOS
permalink: /docs/mac-os
parent: Tips & Tricks
last_modified_date: Dec 04 2021 16:20
---

[//]: # (@formatter:on)

# MacOS tips and tricks

## Always show/hide the hidden files in Finder

```shell
# To show
defaults write com.apple.Finder AppleShowAllFiles true

# To hide
defaults write com.apple.Finder AppleShowAllFiles false

# Restart Finder after that
killall Finder
```

## Delete all executable files in Mac command line

```shell
find . -maxdepth 1 -perm -111 -delete
```