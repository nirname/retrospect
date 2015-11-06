# GIT

## Set a new email

    git config --global user.email "me@example.com"

## Verify the setting

    git config --global user.email

## Remove branch

    git branch -d feature # locally
    git push origin :feature # from remote

## Remove only tag

    git tag -d 12345 # locally
    git push origin :refs/tags/12345 # from remote

## Create repository available for pushes

    git init --bare

## Turn an existing "non-bare" repository into a "bare" \
(with working directory)

    git clone --bare -l non_bare_repo new_bare_repo

## Turn an existing "bare" repository into a "non-bare" \
(without working directory)

    git clone

## Reset the entire repository to the last committed state:

    git reset --hard

## Remove untracked files

    git clean -d -x -f

    # including directories (-d)
    # ignored files (-x)
    # -f argument with
    # -n to perform a dry-run
    # or -i for interactive mode and it will tell you what will be removed.

## Pushing to a Remote Branch with a Different Name

    git push origin local-name:remote-name.

## Reverse ignoring

    * # ignore all
    !/templates # don't ignore directory
    !/templates/* # and files inside
