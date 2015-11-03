# Ubuntu

## Old releases

If your release is unsupported and you cannot use `apt-get` then set other
software sources:

    sudo sed -i -e 's/ca.archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

## How to check version of ubuntu

    lsb_release -a
