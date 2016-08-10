# GIT

## Installation

    apt-get install git-core

## Settings

### Set a new email

    git config --global user.email "me@example.com"

### Verify the setting

    git config --global user.email

### Aliases

Add the following to the `.gitconfig` file in your `$HOME` directory.

    [alias]
      co = checkout
      cm = commit
      st = status
      br = branch
      mr = merge
      hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
      type = cat-file -t
      dump = cat-file -p
      ignore = update-index --assume-unchanged
      unignore = update-index --no-assume-unchanged
      ignored = !git ls-files -v | grep "^[[:lower:]]"
    [core]
      excludesfile = ~/.gitignore


### Diff with Meld

Install `meld`

    sudo apt-get install meld

Add the following to the `.gitconfig` file in your `$HOME` directory.

[diff]
        external = /home/user/diff.py

Put `diff.py` in your home directory

    #!/usr/bin/python

    import sys
    import os

    os.system('meld "%s" "%s"' % (sys.argv[2], sys.argv[5]))

Make it executable

    chmod 755 ~/diff.py

Add to `~/.gitconfig`

    [diff]
      external = ~/diff.py
    [merge]
      tool = meld

## Commands

### Remove branch

    git branch -d feature # locally
    git push origin :feature # from remote

### Remove only tag

    git tag -d 12345 # locally
    git push origin :refs/tags/12345 # from remote

### Create repository available for pushes

    git init --bare

### Turn an existing "non-bare" repository into a "bare"<br/>
(without working directory)

    git clone --bare -l non_bare_repo new_bare_repo

### Turn an existing "bare" repository into a "non-bare"<br/>
(with working directory)

    git clone

### Reset the entire repository to the last committed state:

    git reset --hard

### Remove untracked files

    git clean -d -x -f

    # including directories (-d)
    # ignored files (-x)
    # -f argument with
    # -n to perform a dry-run
    # or -i for interactive mode and it will tell you what will be removed.

### Checkout to branch with different name

    git co -b local-branch remote/remote-branch

### Pushing to a Remote Branch with a Different Name

    git push origin local-name:remote-name.

Easy way:

Set push.default to upstream to push branches to their upstreams (which is the
same that pull will pull from, defined by branch.newb.merge), rather than
pushing branches to ones matching in name (which is the default setting for
push.default, matching)

    git config push.default upstream

Note that this used to be called tracking not upstream before Git 1.7.4.2, so if
you're using an older version of Git, use tracking instead. The push.default
option was added in Git 1.6.4, so if you're on an older version than that, you
won't have this option at all and will need to explicitly specify the branch to
push to.

## Rebase and resolving conflicts

How to resolve conflict while doing rebase.

Choose priority of file while doing `rebase`

    git checkout --ours index.html
    git checkout --theirs _layouts/default.html

Sadly, these options are only in Git versions 1.6.1 and up.
If you have an older version and don’t feel like upgrading,
there’s ways to get around this.

To emulate `--theirs`, we’d do:

    git reset -- _layouts/default.html
    git checkout MERGE_HEAD -- _layouts/default.html

And for `--ours`:

    git reset -- index.html
    git checkout ORIG_HEAD -- index.html

## Ignoring

### Reverse ignoring

    * # ignore all
    !/templates # don't ignore directory
    !/templates/* # and files inside

### Per Project

Use `.gitignore` file in the repository

### Per Repository

You can exclude files on a per repository basis by editing the
`.git/info/excludes` file in your repository

### Per Computer: through settings in ~/.gitconfig

In `.gitconfig` file under the `[core]` section add the path to file for
the `excludesfile` key:

    [core]
        excludesfile = ~/.gitignore

## Subtrees

### Add subtree

Пример из документации: добавляем код из ветки master репозитория Bproject
(лежит в /path/to/B) в наш проект в поддиректорию dir-B/.

    $ git remote add -f Bproject /path/to/B
    $ git merge -s subtree --no-commit Bproject/master
    $ git read-tree --prefix=dir-B/ -u Bproject/master
    $ git commit -m "Merge B project as our subdirectory"

Если не ходим делать лишних коммитов, используем --squash

    $ git merge --squash -s subtree --no-commit Bproject/master

Нужно обратить внимание на ключ -f у git remote add.
Он говорит гиту сразу сделать fetch этого remote-а.

В дальнейшем, изменения в Bproject подтягиваются командой git pull с явным
указанием нужной ветки и стратегии объединения:

    $ git pull -s subtree Bproject master

Если в рабочей копии не добавлен соответствующий remote-у поддерева, в истории
основного репозитория не показывается имя ветки, из которой притянуты изменения.

Проблема чисто косметическая, и на работу не влияет. Лечится добавлением этого
remote-а в рабочую копию:

    $ git remote add -f Bproject /path/to/B

В дальнейшем, если появляются новые ветки, можно подтягивать изменения в remote:

    $ git fetch Bproject

### Extract as subtree

    git checkout subbranch
    git filter-branch --subdirectory-filter subdirectory -- --all
    git filter-branch --subdirectory-filter doc -- --all

## Spesifying Revisions

See [git-rev-parse](http://schacon.github.io/git/git-rev-parse#_specifying_revisions).

Here is an illustration, by Jon Loeliger. Both commit nodes B and C are parents
of commit node A. Parent commits are ordered left-to-right.

    G   H   I   J
     \ /     \ /
      D   E   F
       \  |  / \
        \ | /   |
         \|/    |
          B     C
           \   /
            \ /
             A

    A =      = A^0
    B = A^   = A^1     = A~1
    C = A^2  = A^2
    D = A^^  = A^1^1   = A~2
    E = B^2  = A^^2
    F = B^3  = A^^3
    G = A^^^ = A^1^1^1 = A~3
    H = D^2  = B^^2    = A^^^2  = A~2^2
    I = F^   = B^3^    = A^^3^
    J = F^2  = B^3^2   = A^^3^2
