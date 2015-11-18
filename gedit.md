# Gedit

## Plugins

**Package of plugins**

    sudo apt-get install gedit-gmate gedit-plugins

**Markdown preview dependencies**

    sudo apt-get install python3-markdown gir1.2-webkit-3.0

**EditorConfig**

    python3-setuptools
    https://pypi.python.org/pypi/EditorConfig
    http://editorconfig.org/

    sudo apt-get install python-pip
    pip install editorconfig

    $ cd editorconfig_plugin
    $ ./install.sh
    $ cd editorconfig-core-py
    $ sudo python setup.py install

**Hard word wrap**

> Use `Ctrl + J` for joining lines & `Ctrl + Shift + J` for splitting them

A hard word wrap or line break feature isn’t included in gedit by default,
but it’s easily added by using the ‘External Tools’ plugin and a
two-liner shell script. This will allow you to format your documents with a
line break at column 80, or whatever you’d like it to be, by selecting the
text, paragraph, or entire document and applying the shell script. Here’s
how...

1. Open gedit
2. Navigate to Edit -> Preferences -> Plugins
3. Enable “External Tools” and press “Configure Plugin”
4. Press “New” and enter “Line Break at Col 80” (or any name you like)
5. Paste the following script in the “command(s)” text area (you can
choose to leave out the #comments, these are only here as a reminder in case
you want to modify it to fit your needs):

Bash script:

    #!/bin/sh

    BREAK=80

    # fmt [-WIDTH][OPTION]... [FILE]...
    # --uniform-spacing -- one space between words, two after sentences
    # --split-only -- split long lines, but do not refill
    # --width=WIDTH -- maximum line width (default of 75 columns)
    # when FILE is -, read standard input

    fmt --uniform-spacing --split-only --width $BREAK -

6. Choose “Current selection” as Input
7. Choose “Replace current selection” as Output
8. At this point, you can choose to create a shortcut key such as “ctrl+m” for
easy access.
8. Close “External Tools Manager” by pressing the “Close” button
9. Now this script is executable under the “Tools” menu. Alternatively, you can
use your shortcut key for quick access.

The next step would be to somehow get gedit to automatically perform these
hard wraps as your typing (like the evolution email client does). If anybody
has a suggestion, I’d love to hear about it in the comments below. I’m
very surprised that this isn’t included in the already many featured
gedit program by default, but thankfully it’s very easily remedied with
the method described above.

Look at the [text wrap plugin](http://hartmann-it-design.de/gedit/TextWrap/)

## Where to find gedit styles & highlights

    ~/.local/share/gtksourceview-2.0/styles/
    /usr/share/gnome/gtksourceview-2.0/styles/
    /usr/local/share/gtksourceview-2.0/styles/
    /usr/share/gtksourceview-2.0/styles/

    /usr/share/gtksourceview-3.0/styles/
    ~/.local/share/gedit/styles

    /usr/share/gtksourceview-3.0/language-specs/

    /usr/lib/gedit/plugins
