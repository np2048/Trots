
# Zathura

[Zathura](https://pwmt.org/projects/zathura/) is a lightweight and minimalistic document viewer. There are plugins for reading PDF, DejaVu, PostScript and Comic Book documents.

## Hotkeys

**/, ?** — search for text.

**n, N** — search for the next or previous result.

**mX** — set a quickmark to a letter or number X.

**'X** — goto quickmark saved at letter or number X.

**R** — reload document.

**zI, zO, z0** — zoom in, out or to the original size.

**a** — adjust the document to page-fit.

**s** — adjust the document to fit width.

**r** — rotate pages.

**Ctrl+r** — recolor pages (toggle black & white mode).

Most of vi's movement/scrolling commands are supported.

## Commands 

Commands may be entered directly into *zathura* by pressing 

    :

just like in *vi*. 

**exec** — execute an external command.

**bmark** — save a bookmark.

**bdelete** — delete a bookmark.

**blist** — list bookmarks.

Commands in the same format may be entered in the [configuration file](#config).

<a name='config'></a>

## Zathura configuration file


It can be configured via a file located at *$XDG_CONFIG_HOME/zathura/zathurarc* (default: ~/.config/zathura/zathurarc):

    $ vim ~/.config/zathura/zathurarc

It that file doesn't exist you may create it.

You can configure the viewer by adding commands into this file.

## Colors

You can adjust background and font face colors:

    set recolor true
    set recolor-lightcolor "#2C4441"
    set recolor-darkcolor "#B6D0CD"

## Enable copy to clipboard

    set selection-clipboard clipboard

## Read more

[Zathura documentation at the official site.](https://pwmt.org/projects/zathura/documentation/)

[Man page with keyboard shortcuts](https://github.com/pwmt/zathura/blob/master/doc/man/zathura.1.rst)
