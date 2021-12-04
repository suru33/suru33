---

[//]: # (@formatter:off)
layout: page
title: SSH Key
permalink: /docs/dev/ssh-key
parent: Developer
grand_parent: Tips & Tricks
last_modified_date: Dec 04 2021 16:20
---
[//]: # (@formatter:on)

# Generating a new SSH key and adding it to the ssh-agent

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

eval "$(ssh-agent -s)"
```

## MacOS

```bash
~/.ssh/config

Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa


ssh-add -K ~/.ssh/id_rsa 
# -K is deprecated in new versions of MacOS

ssh-add --apple-use-keychain ~/.ssh/id_rsa
```

## Windows/Linux

```bash
ssh-add ~/.ssh/id_rsa
```
