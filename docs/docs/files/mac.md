---

[//]: # (@formatter:off)
layout: page
title: MacOS
permalink: /docs/mac-os
parent: Tips & Tricks
last_modified_date: Dec 28 2022 17:58
---

[//]: # (@formatter:on)

# MacOS tips and tricks

## Always show/hide the hidden files in Finder

```shell
# To show
defaults write com.apple.Finder AppleShowAllFiles TRUE

# To hide
defaults write com.apple.Finder AppleShowAllFiles TRUE

# Restart Finder after that
killall Finder
```

## Screenshot

### Change default location

```shell
defaults write com.apple.screencapture location ~/Desktop/screenshots
```

### Change default name

```shell
defaults write com.apple.screencapture name "name"
```

> Restart `SystemUIServer` after those changes

```shell
killall SystemUIServer
```

## Delete all executable files in Mac command line

```shell
find . -maxdepth 1 -perm -111 -delete
```