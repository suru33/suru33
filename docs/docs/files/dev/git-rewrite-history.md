---

[//]: # (@formatter:off)
layout: page
title: Rewrite git commit history
permalink: /docs/dev/rewrite-git-history
parent: Developer
grand_parent: Tips & Tricks
last_modified_date: Dec 04 2021 16:20
---
[//]: # (@formatter:on)

# Rewrite git commit history

### Check list of authors

```sh
git log --pretty=full | grep  -E '(Author|Commit): (.*)$' | sed 's/Author: //g' | sed 's/Commit: //g' | sort -u
```

### Change history

```shell
git filter-branch --env-filter '
    if [ "$GIT_COMMITTER_EMAIL" = "<OLD AUTHOR EMAIL - 1>" ]; then
        export GIT_COMMITTER_NAME="<NEW AUTHOR NAME>"
        export GIT_COMMITTER_EMAIL="<NEW AUTHOR EMAIL>"
    fi
    if [ "$GIT_COMMITTER_EMAIL" = "<OLD AUTHOR EMAIL - 2 ... >" ]; then
        export GIT_COMMITTER_NAME="<NEW AUTHOR NAME>"
        export GIT_COMMITTER_EMAIL="<NEW AUTHOR EMAIL>"
    fi
' --tag-name-filter cat -f -- --all
```

### Push the code

```sh
git push --force --tags origin 'refs/heads/*'
```