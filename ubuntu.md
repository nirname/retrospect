# Ubuntu

## Old releases

If your release is unsupported and you cannot use `apt-get` then set other
software sources:

    sudo sed -i -e 's/ca.archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

## How to check version of ubuntu

    uname -a
    lsb_release -a

## Managing users

    useradd -m username -s /bin/bash
    passwd username

## Generate password

    pwgen -syn 10 1

## Encrypting files

    gpg -c file
    gpg --decrypt file

## Output middle of a file

    tail -n +5 file # from specific line
    |
    head -n 5 # till specific line

## Print one file at one line

    ls -1

## Copy the last file to new named by date

    ls -Q | sort | tail -n 1 | xargs cat > "`date +tasks\ %Y-%m-%d.txt`"
