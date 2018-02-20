# Gedit

## Plugins

**Package of plugins**

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa && sudo apt-get update
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

## Hotkeys

Look at

    ~/.config/gedit/accels

## Snippets

This is copy of [this article](http://www.tuxradar.com/content/save-time-gedit-snippets) I wanted to save

---

Some people think that Gedit is a toy text editor not suitable for more
experienced users. And while it might lack Emacs's psychiatrist or Vim's undo
branching, it turns out that Gedit has a lot of power under its hood - if you
know where to look.

One feature that is guaranteed to save you time is Snippets, a plugin that
enables quick insertion of commonly used text, and something we use frequently
here on TuxRadar. We're going to show you how to get started using the built-in
snippets, and how you can use shell commands and even Python code to make your
own...

You see, a lot of our content is drawn from the archives of Linux Format
magazine, a magazine that is produced using Mac OS X, Adobe InDesign and a dozen
other proprietary tools. No, it's not ideal, but sadly we have little say in the
matter. Besides, you don't think the folks behind Cross Stitcher magazine stitch
their magazine together, do you?

Anyway, the problem with converting articles from the magazine world to the
internet world is the need to replace special symbols with more simple
equivalents. Magazines, for example, make extensive use of curly quotes, em- and
en-dashes, ellipses (...), non-breaking spaces and more. And while these do have
HTML equivalents, they are rarely used, so we strip all these out and replace
them with simple ASCII characters.

Once that's done, we need to convert articles to HTML, and that's what takes the
real time. Or at least it did - until we started using Snippets. You see,
Snippets allows you to insert pre-defined blocks of text either by using a
keystroke or tab completion. That's not an uncommon feature in a text editor,
admittedly, but Snippets makes it particularly easy to create more advanced
placeholders for text replacement, even allowing output from the shell and
Python scripts.

Before we get started with some example snippets, you need to make sure you have
the Snippets plugin enabled. Fire up Gedit and go to Edit > Preferences. From
the Plugins tab, scroll down and make sure Snippets is checked. Once that's done
you should see the Configure Plugin button become active - that's where we'll be
doing most of our work.


### A basic snippet

Copy and paste this into your Gedit window:

    He thrusts his fists
    Against the posts
    And still insists
    He sees the ghosts.

That gives you four simple lines of text. Save that file as test.html - it
doesn't really matter where. But what does matter is that Gedit now knows your
file is HTML, which means Snippets knows too and will activate its list of HTML
snippets. For example, if you select the whole first line and press Shift+Alt+W,
it will automatically be wrapped in a <p> tag, like this:

    <p>He thrusts his fists</p>

What's more, Gedit will automatically leave the first "p" highlighted so that
you can replace it just by typing, and any changes you make will be copied
across to the </p> tag so that it matches. To see how this works, go back to the
Configure Plugin window for Snippets (you'll also find it under Tools > Manage
Snippets) then look inside the HTML category for the snippet called "Wrap
Selection in Open/Close Tag".

When you select that snippet, the code behind it will appear in the top-right of
the window, and should look like this:

    <${1:p}>$GEDIT_SELECTED_TEXT</${1}>

$1 is a placeholder, which means it's something you want to type into after the
snippet has been inserted. In this case, there's only one placeholder, $1, but
it appears twice. Because the same placeholder number has been used twice -
known as a "mirror placeholder" - Gedit will ensure that whatever you type in
the first $1 will be synchronised with the second $1, which is how you can
change `<p>` to `<h1>` and it will be changed in the closing tag too.

The ":p" part of the snippet sets a default value, in this case the HTML
paragraph tag, "p". If you leave off the default value, Gedit will just leave a
blank spot for you to type.

Finally, the most important part: $GEDIT_SELECTED_TEXT. This is a special value
inside snippets that will be automatically replaced with the contents of
whatever text you had selected before the snippet was used. You'll be using this
a lot!

### Working with multiple placeholders

That basic snippet had just one placeholder, which meant that it prompted you to
edit only one piece of text. A slightly more complicated snippet is called "Wrap
Selection as Link", and has two placeholders. To test it out, select the second
of your text lines and press Shift+Alt+L. You should see this:

    <a href="http://somesite.com/">Against the posts</a>

After the snippet has run, Gedit will leave the insertion cursor over
"http://somesite.com/" with that text highlighted so you can replace it by
typing. Type http://www.tuxradar.com in there and then - this is the important
bit - press Tab. When you do that, Gedit will move the caret to "Against the
posts" and select it just as it had selected "http://somesite.com/". That's
because this snippet has two placeholders defined: "$1:http://www.somesite.com/"
and "$2:GEDIT_SELECTED_TEXT".

You can have as many of these placeholders as you need, and any number of them
can have default values specified - just press Tab to move between them.

### Bringing in output from the shell

We're going to create a new snippet from scratch to show off some of the more
advanced features of Snippets. Go to Tools > Manage Snippets to bring up the
Snippets Manager, then scroll up to the top of the category list to where it
says "Global".

The Snippets Manager lets you create and edit your own snippets across a number
of different languages.

Select that, then click the Create New Snippet button (it's just above the Help
button at the bottom of the window).

Call your new snippet "Insert file" and put the following inside it:

    $(1:cat $GEDIT_SELECTED_TEXT)

Notice how that uses standard parentheses (ie "(" and ")") rather than braces
("{" and "}") - that's because the parts inside the parentheses will be sent to
a shell, executed, then be replaced with whatever the shell command prints out.

What that code example does is run "cat" on a filename, with the filename being
specified as $GEDIT_SELECTED_TEXT so all you have to do is type a filename into
Gedit, select it, then run the snippet. Underneath the text area for entering
snippets are some text boxes marked "Activation". Click inside the Shortcut Key
box then press any shortcut you want to assign to this snippet and it will
become active immediately.

You can run any shell commands you like, as long as they return their output
back using stdout. For example, the "bc" mixed with Gedit Snippets means we can
create a simple calculator. In the Snippets Manager, create a new snippet under
the Global category called Calculator. Give it this text:

$(1:echo $GEDIT_SELECTED_TEXT | bc)

Give it the shortcut Ctrl+Shift+C, then click Close and type this into your
Gedit file:

5 + 10 / 2 * 9

Select it all, then press Ctrl+Shift+C to see your text replaced with the answer
to the calculation: 50.

Gedit detects the end of the shell command by looking for a closing parenthesis
(")"), so if your command includes one you need to put a backslash before it,
like this:

$(1:echo "This is a (test\)" > file.txt)

That will save the text "This is a test" to file.txt. As you can see, there is
no need to escape the opening parenthesis ("(").

### Mixing in some Python

Here's where Snippets really starts to prove its worth: you can run Python code
wherever and whenever you want to. Let's start with a simplified example of a
snippet we use here on TuxRadar to kill off curly quotes:

    $< return $GEDIT_SELECTED_TEXT.replace('“', '"') >

That is designed to convert this:

    “Hello, world!”

...into this:

    "Hello, world!"

The "$<" part signals the beginning of your Python code, and it ends with the
corresponding ">" at the end of the snippet. In between is a call to the
replace() method of a Python string - in this case, $GEDIT_SELECTED_TEXT - which
replaces a curly quote with a simple ASCII one.

When you've finished making all your changes to the input, you hand any output
back to Gedit using Python's "return" statement.

That initial snippet fixes the opening curly quote, but not the closing curly
quote, which is easily fixed simply by making the snippet span more than one
line, like this:

    $<
    output = $GEDIT_SELECTED_TEXT.replace('“', '"')
    output = output.replace('”', '"')
    return output
    >

If you're obsessed with brevity, you could write that as a one-liner using
something like this:

    $<return $GEDIT_SELECTED_TEXT.replace('“', '"').replace('”', '"') >

As with shell placeholders, you need to be sure to escape the end symbol if
needed, which in the case of Python placeholders is >. To give you a working
example of this, consider our original text:

    He thrusts his fists
    Against the posts
    And still insists
    He sees the ghosts.

If you wanted to put <p> tags around each of those lines, you could select each
line individually and use Shift+Alt+W. But with Python we can select the whole
paragraph, split it by new lines, then add HTML tags for each line, like this:

    $<
    lines = $GEDIT_SELECTED_TEXT.split("\n");
    output = "";
    for line in lines:
      output += "<p\>" + line + "</p\>\n";
    return output
    >

What that does is split up the selected text by line breaks, then loop over each
line and add it along with the <p> start and end tags to the output. However,
because <p> and </p> both contain the > symbol, Gedit will think that means the
end of your Python snippet. So, the solution is to put a \ before the > so that
Gedit ignores it.

Note that we've used "\n" to add line breaks of our own into the output to keep things neat.

### Converting tabs to tables

Copy and paste this into your Gedit document:

    a	apples
    b	bananas
    c	cherries
    d	dates

That's a list of items, one per line, where the item on the left is separated
from the item on the right by a tab character. This is a fairly common way to
work with tables in plain-text, but with a bit of Gedit + Snippets + Python
magic we can whip that up into a real HTML table.

What we need to do is simple:

    Split the selected text by line break
    Loop over each line
    Split each line by tab
    Add HTML table tags

...while remembering that any time we want to print > we need to put a \ before
it. Here's how to do that in Python:

    $<
    lines = $GEDIT_SELECTED_TEXT.split("\n");
    output = '<table\>\n';

    for line in lines:
      output += '<tr\>';

      columns = line.split("\t");
      for item in columns:
      output += '<td\>' + item + '</td\> '

      output += '</tr\>\n';

    output += '</table\>';
    return output
    >

If you assign that to a shortcut, then select the four lines from before and run the snippet, you'll get this:

    <table>
    <tr><td>a</td> <td>apples</td> </tr>
    <tr><td>b</td> <td>bananas</td> </tr>
    <tr><td>c</td> <td>cherries</td> </tr>
    <tr><td>d</td> <td>dates</td> </tr>
    </table>

If you wanted to be a bit more fancy and include some zebra stripes for your
table rows, just drop in a counter variable and use modulo (%) to check whether
it's odd or even, like this:

    $<
    lines = $GEDIT_SELECTED_TEXT.split("\n")
    output = '<table\>\n'
    counter = 0

    for line in lines:
      if counter % 2 == 0:
        output += '<tr class="even"\>'
        else:
        output += '<tr class="odd"\>'

        columns = line.split("\t")
      for item in columns:
        output += '<td\>' + item + '</td\> '

      output += '</tr\>\n'
      counter += 1

    output += '</table\>'
    return output
    >

### Some last tips

There's a huge amount you can do with Snippets, particularly when you start
taking advantage of shell and Python placeholders. But before we let you run
free, here are three last pointers:

    You can use the $0 placeholder to specify the last position that should be jumped to. By default this is the end of your snippet, but if you use $0 you can choose somewhere else.
    Along with $GEDIT_SELECTED_TEXT, you can also use $GEDIT_FILENAME and $GEDIT_BASENAME to use the full filename (eg /home/tuxradar/foo.bar) and the base filename (eg foo.bar) in your snippets.
    When you've arranged all your snippets just as you want them, go into the Snippets Manager and click the save icon to export selected snippets as XML so you can copy them other machines.

Have fun - and make sure you take a look through some of the awesome snippets
that are included by default!
