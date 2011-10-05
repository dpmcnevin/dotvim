# DotVim

These are my .vim customization files, copied wholesale from
[Janus](http://github.com/carlhuda/janus) and then switched all the
plugins over to [pathogen](http://github.com/tpope/vim-pathogen) and
added a few more of use to me.


## Installation

    git clone git://github.com/dpmcnevin/dotvim.git ~/.vim
    (cd .vim && mkdir -p backup && git submodule init && git submodule update)

## Updating to the latest version of plugins

    (cd .vim && git submodule foreach git pull)

# Intro to VIM

Here's some tips if you've never used VIM before:

## Tutorials

* Type `vimtutor` into a shell to go through a brief interactive
  tutorial inside VIM.
* Read the slides at [VIM: Walking Without Crutches](http://walking-without-crutches.heroku.com/#1).
* Watch the screencasts at [vimcasts.org](http://vimcasts.org/)
* Watch Derek Wyatt's energetic tutorial videos at [his site](http://www.derekwyatt.org/vim/vim-tutorial-videos/)
* Read wycats' perspective on learning vim at
  [Everyone who tried to convince me to use vim was wrong](http://yehudakatz.com/2010/07/29/everyone-who-tried-to-convince-me-to-use-vim-was-wrong/)
* Read this and other answers to a question about vim at StackOverflow:
  [Your problem with Vim is that you don't grok vi](http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim/1220118#1220118)

## Modes

* VIM has two modes:
  * insert mode- stuff you type is added to the buffer
  * normal mode- keys you hit are interpretted as commands
* To enter insert mode, hit `i`
* To exit insert mode, hit `<ESC>`

## Useful commands

* Use `:q` to exit vim
* Certain commands are prefixed with a `<Leader>` key, which maps to `\`
  by default. Use `let mapleader = ","` to change this.
* Keyboard [cheat sheet](http://walking-without-crutches.heroku.com/image/images/vi-vim-cheat-sheet.png).

# Features

This vim distribution includes a number of packages built by others.

## Base Customizations

Janus ships with a number of basic customizations for vim:

* Line numbers
* Ruler (line and column numbers)
* No wrap (turn off per-buffer via set :wrap)
* Soft 2-space tabs, and default hard tabs to 2 spaces
* Show tailing whitespace as `.`
* Make searching highlighted, incremental, and case insensitive unless a
  capital letter is used
* Always show a status line
* Allow backspacing over everything (identations, eol, and start
  characters) in insert mode
* `<Leader>e` expands to `:e {directory of current file}/` (open in the
  current buffer)
* `<Leader>te` expands to `:te {directory of current file}/` (open in a
  new MacVIM tab)
* `<C-P>` inserts the directory of the current file into a command

## "Project Drawer" aka [NERDTree](http://github.com/wycats/nerdtree)

NERDTree is a file explorer plugin that provides "project drawer"
functionality to your vim projects.  You can learn more about it with
:help NERDTree.

**Customizations**: Janus adds a number of customizations to the core
NERDTree:

* Use `<Leader>n` to toggle NERDTree
* Ignore `*.rbc` and `*~` files
* Automatically activate NERDTree when MacVIM opens and make the
  original buffer the active one
* Provide alternative :e, :cd, :rm and :touch abbreviations which also
  refresh NERDTree when done (when NERDTree is open)
* When opening vim with vim /path, open the left NERDTree to that
  directory, set the vim pwd, and clear the right buffer
* Disallow `:e`ing files into the NERDTree buffer
* In general, assume that there is a single NERDTree buffer on the left
  and one or more editing buffers on the right

## [Ack.vim](http://github.com/mileszs/ack.vim)


Ack.vim uses ack to search inside the current directory for a pattern.
You can learn more about it with :help Ack

**Customizations**: Janus rebinds command-shift-f (`<D-F>`) to bring up
`:Ack `.

## [Align](http://github.com/tsaleh/vim-align)

Align lets you align statements on their equal signs, make comment
boxes, align comments, align declarations, etc.

* `:5,10Align =>` to align lines 5-10 on `=>`'s

## [Command-T](https://wincent.com/products/command-t)

Command-T provides a mechanism for searching for a file inside the
current working directory. It behaves similarly to command-t in
Textmate.

**Customizations**: Janus rebinds command-t (`<D-t>`) to bring up this
plugin. It defaults to `<Leader>t`.

## [ConqueTerm](http://code.google.com/p/conque/)

ConqueTerm embeds a basic terminal inside a vim buffer. The terminal has
an insert mode in which you can type commands, tab complete and use the
terminal like normal. You can also escape out of insert mode to use
other vim commands on the buffer, like yank and paste.

**Customizations**: Janus binds command-e (`<D-e>`) to bring up
`:ConqueTerm bash --login` in the current buffer.

**Note**: To get colors working, you might have to `export TERM=xterm`
and use `ls -G` or `gls --color`

## [indent\_object](http://github.com/michaeljsmith/vim-indent-object)

Indent object creates a "text object" that is relative to the current
ident. Text objects work inside of visual mode, and with `c` (change),
`d` (delete) and `y` (yank). For instance, try going into a method in
normal mode, and type `v ii`. Then repeat `ii`.

**Note**: indent\_object seems a bit busted. It would also be nice if
there was a text object for Ruby `class` and `def` blocks.

## [surround](http://github.com/tpope/vim-surround)

Surround allows you to modify "surroundings" around the current text.
For instance, if the cursor was inside `"foo bar"`, you could type
`cs"'` to convert the text to `'foo bar'`.

There's a lot more; check it out at `:help surround`

## [NERDCommenter](http://github.com/ddollar/nerdcommenter)

NERDCommenter allows you to wrangle your code comments, regardless of
filetype. View `:help NERDCommenter` for all the details.

**Customizations**: Janus binds command-/ (`<D-/>`) to toggle comments.

## [SuperTab](http://github.com/ervandew/supertab)

In insert mode, start typing something and hit `<TAB>` to tab-complete
based on the current context.

## ctags

Janus includes the [TagList](http://github.com/vim-scripts/taglist.vim)
plugin, which binds `:Tlist` to an overview panel that lists all ctags
for easy navigation.

**Customizations**: Janus binds `<Leader>rt` to the ctags command to
update tags.

**Note**: For full language support, run `brew install ctags` to install
exuberant-ctags.

**Tip**: Check out `:help ctags` for information about VIM's built-in
ctag support. Tag navigation creates a stack which can traversed via
`Ctrl-]` (to find the source of a token) and `Ctrl-T` (to jump back up
one level).

## Git Support ([Fugitive](http://github.com/tpope/vim-fugitive))

Fugitive adds pervasive git support to git directories in vim. For more
information, use `:help fugitive`

Use `:Gstatus` to view `git status` and type `-` on any file to stage or
unstage it. Type `p` on a file to enter `git add -p` and stage specific
hunks in the file.

Use `:Gdiff` on an open file to see what changes have been made to that
file

## [Gist-vim](http://github.com/mattn/gist-vim)

Nice [gist integration](https://github.com/mattn/gist-vim) by mattn.
Requires exporting your `GITHUB_TOKEN` and `GITHUB_USER` as environment
variables or setup your [GitHub token config](http://help.github.com/git-email-settings/).

Try `:Gist`, `:Gist -p` and visual blocks.

## [ZoomWin](http://github.com/vim-scripts/ZoomWin)

When working with split windows, ZoomWin lets you zoom into a window and
out again using `Ctrl-W o`

**Customizations**: Janus binds `<Leader><Leader>` to `:ZoomWin`

