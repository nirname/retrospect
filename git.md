# GIT

## Settings

# Installations

  apt-get install git-core

### Set a new email

    git config --global user.email "me@example.com"

### Verify the setting

    git config --global user.email

## Working

### Remove branch

    git branch -d feature # locally
    git push origin :feature # from remote

### Remove only tag

    git tag -d 12345 # locally
    git push origin :refs/tags/12345 # from remote

### Create repository available for pushes

    git init --bare

<h3> Turn an existing "non-bare" repository into a "bare"<br/>
(without working directory)</h3>

    git clone --bare -l non_bare_repo new_bare_repo

<h3>Turn an existing "bare" repository into a "non-bare" <br/>
(with working directory)</h3>

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

### Pushing to a Remote Branch with a Different Name

    git push origin local-name:remote-name.

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

## Subtree

Пример из документации: добавляем код из ветки master репозитория Bproject
(лежит в /path/to/B) в наш проект в поддиректорию dir-B/.

    $ git remote add -f Bproject /path/to/B
    $ git merge -s ours --no-commit Bproject/master
    $ git read-tree --prefix=dir-B/ -u Bproject/master
    $ git commit -m "Merge B project as our subdirectory"

Если не ходим делать лишних коммитов, используем --squash

    $ git merge --squash -s ours --no-commit Bproject/master

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
