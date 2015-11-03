# Firefox

## Manual Installation

The following instructions will install Firefox in your home directory, and will use a different profile for Mozilla and Ubuntu builds of Firefox.

* Go to the Firefox download page

* Download Firefox for Linux

* Extract the file you downloaded into `~/firefox` (e.g. by doing `tar jxf firefox*.tar.bz2 -C $HOME`)

* Make a backup of your `~/.mozilla` directory (e.g. by doing `tar zcPf ~/mozilla-backup-$(date +%s).tar.gz ~/.mozilla`)

Next, if this is the first time you have installed a Mozilla build, do the following:

* Quit any instances of Firefox you have open.

* Run ~/firefox/firefox -ProfileManager to start the Firefox profile manager

* Create a new profile called mozilla-build

* Make sure that the default profile is still selected

* Click exit to close the profile manager (do not start Firefox)

* Run the following shell script:

    mkdir ~/bin
    cat > ~/bin/firefox <<END
    #!/bin/bash

    exec "\$HOME/firefox/firefox" -P mozilla-build "\$@"
    END
    chmod 755 ~/bin/firefox

The firefox command in your ~/bin directory will now run Firefox with the mozilla-build profile.

## Uninstallation

* Delete the ~/firefox directory and the ~/bin/firefox file

* Run firefox -ProfileManager and delete mozilla-build

This completely uninstalls the Mozilla build of Firefox. If you install a Mozilla build in future, you will need to perform all of the instructions above, including the first time instructions.

## Restore your old profile

To restore the backup of your profile, do the following:

* Close any open Firefox windows

* Rename ~/.mozilla (e.g. mv ~/.mozilla ~/.mozilla-broken)

* Extract your archive (e.g. by doing tar zxPf ~/mozilla-backup-DATE.tar.gz

This will completely reset your Firefox profile to the point when you made the backup.



## Change icon


1. Edit the ‘firefox.desktop’

The ‘.desktop’ files are usually stored in “/usr/share/applications/”. For some applications that are installed in user’s directory, you may find the .desktop files in “~/.local/share/applications/” directory.

To edit the firefox.desktop, press Ctrl+Alt+T on keyboard to open terminal. When it opens, run:

    cd /usr/share/applications
    sudo gedit firefox.desktop

edit firefox.desktop

It will navigate to /usr/share/applications/ directory and open the firefox.desktop file via gedit editor. You can run ls |more to list all available files in that directory.

2. Change the value of Icon

In gedit window, scroll down to find out the line that starts with “Icon=” and change its value to the exact path to your NEW icon file. The image is usually .png file in 64×64 or 128×128.
