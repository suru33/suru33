---

[//]: # (@formatter:off)
layout: page
title: Rewrite git commit messages
permalink: /docs/dev/rewrite-git-commit-messages
parent: Developer
grand_parent: Tips & Tricks
last_modified_date: Dec 04 2021 16:20
---
[//]: # (@formatter:on)

# Rewrite git commit messages

```shell
git rebase --interactive commit_hash^
```

- Using `vi/vim` you change the words `pick` to `reword` for the commits you want to change, save and `quit(:wq)`.
- Then git will prompt you with each commit that you marked as reword, so you can change the commit message.
- Each commit message you have to save and `quit(:wq)` to go to the next commit message
