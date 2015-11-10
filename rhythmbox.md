# Rhythmbox

    ~/.local/share/rhythmbox
    ~/.cache/rhythmbox
    ~/.gconf/apps/rhythmbox.

You can use your file browser to do this or run this command from the terminal:

    rm ~/.local/share/rhythmbox/ ~/.cache/rhythmbox/ ~/.gconf/apps/rhythmbox/ -r

There are a couple of ways to edit the locations information - either
graphically using `dconf-editor` or via the terminal using gsettings.

**First the graphical way**.

Install the package `dconf-tools`. In the dash press Alt+F2 and type
`dconf-editor`. Find `org->gnome->rhythmbox->rhythmdb` and edit the locations

**Using `gsettings`**:

    gsettings get org.gnome.rhythmbox.rhythmdb locations
    ['file:///home/dad/Music', 'file:///home/dad/.ubuntuone/Purchased%20from%20Ubuntu%20One']
    gsettings set org.gnome.rhythmbox.rhythmdb locations "['file:///home/dad/Music', 'file:///media/musiclibrary/mymusic']"

    gsettings reset-recursively org.gnome.rhythmbox
    gsettings reset-recursively org.gnome.rhythmbox.display-page-tree
    gsettings reset-recursively org.gnome.rhythmbox.library
    gsettings reset-recursively org.gnome.rhythmbox.player
    gsettings reset-recursively org.gnome.rhythmbox.plugins
    gsettings reset-recursively org.gnome.rhythmbox.plugins.iradio
    gsettings reset-recursively org.gnome.rhythmbox.plugins.lyrics
    gsettings reset-recursively org.gnome.rhythmbox.plugins.magnatune
    gsettings reset-recursively org.gnome.rhythmbox.plugins.replaygain
    gsettings reset-recursively org.gnome.rhythmbox.plugins.visualizer
    gsettings reset-recursively org.gnome.rhythmbox.podcast
    gsettings reset-recursively org.gnome.rhythmbox.podcast
    gsettings reset-recursively org.gnome.rhythmbox.rhythmdb
    gsettings reset-recursively org.gnome.rhythmbox.sharing
    gsettings reset-recursively org.gnome.rhythmbox.sources
