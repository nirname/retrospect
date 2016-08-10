# Ubuntu

## Old releases

If your release is unsupported and you cannot use `apt-get` then set other
software sources:

    sudo sed -i -e 's/ca.archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

## How to check version of ubuntu

    uname -a
    lsb_release -a

## Managing users

    sudo useradd user
    sudo useradd -m username -s /bin/bash
    sudo passwd username

    sudo usermod -a -G sudo user

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

## List of opened ports

    sudo lsof -i
    sudo netstat -lptu
    sudo netstat -tulpn

## Directory of shell command

    type -a command

# Making scripts run at boot time with Debian

Posted by Steve on Mon 11 Oct 2004 at 13:01
Tags: boot, debian-specific commands, initscripts, scheduling

Debian uses a Sys-V like init system for executing commands when the system runlevel changes - for example at bootup and shutdown time.

If you wish to add a new service to start when the machine boots you should add the necessary script to the directory /etc/init.d/. Many of the scripts already present in that directory will give you an example of the kind of things that you can do.

Here's a very simple script which is divided into two parts, code which always runs, and code which runs when called with "start" or "stop".

    #! /bin/sh
    # /etc/init.d/blah
    #

    # Some things that run always
    touch /var/lock/blah

    # Carry out specific functions when asked to by the system
    case "$1" in
      start)
        echo "Starting script blah "
        echo "Could do more here"
        ;;
      stop)
        echo "Stopping script blah"
        echo "Could do more here"
        ;;
      *)
        echo "Usage: /etc/init.d/blah {start|stop}"
        exit 1
        ;;
    esac

    exit 0

Once you've saved your file into the correct location make sure that it's executable by running "chmod 755 /etc/init.d/blah".

Then you need to add the appropriate symbolic links to cause the script to be executed when the system goes down, or comes up.

The simplest way of doing this is to use the Debian-specific command update-rc.d:

    root@skx:~# update-rc.d blah defaults
     Adding system startup for /etc/init.d/blah ...
       /etc/rc0.d/K20blah -> ../init.d/blah
       /etc/rc1.d/K20blah -> ../init.d/blah
       /etc/rc6.d/K20blah -> ../init.d/blah
       /etc/rc2.d/S20blah -> ../init.d/blah
       /etc/rc3.d/S20blah -> ../init.d/blah
       /etc/rc4.d/S20blah -> ../init.d/blah
       /etc/rc5.d/S20blah -> ../init.d/blah

If you wish to remove the script from the startup sequence in the future run:

    root@skx:/etc/rc2.d# update-rc.d -f  blah remove
    update-rc.d: /etc/init.d/blah exists during rc.d purge (continuing)
     Removing any system startup links for /etc/init.d/blah ...
       /etc/rc0.d/K20blah
       /etc/rc1.d/K20blah
       /etc/rc2.d/S20blah
       /etc/rc3.d/S20blah
       /etc/rc4.d/S20blah
       /etc/rc5.d/S20blah
       /etc/rc6.d/K20blah

This will leave the script itself in place, just remove the links which cause it to be executed.

You can find more details of this command by running "man update-rc.d".
