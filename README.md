# Console Syntax Highlighting

While writing a Pandoc Markdown-based guide about creating a
[Linux Home Server][home-server] I spent some time understanding issues
and finding solutions.  I then added another guide on
[getting started][doc-with-pandoc-md] with Markdown-based technical guides.

One of the issues I have dealt with on both occasions is *console*
input/output and syntax-highlighting.  When you are helping others
understand command line options it is very useful to **highlight**
command line console sessions.

Pandoc uses the Haskell *skylighting* library for syntax highlighting.  The
highlighting descriptions are written in XML, using XML syntax descriptions
designed for [KDE's Kate syntax highlighting][kde-syntax-hi].

By adding Kate syntax highlighting I was able to present console sessions
as fenced code blocks with more interesting syntax highlighting in 
Pandoc-generated Markdown-based documents.

By adding Vim syntax highlighting for my favourite editor, Gvim
(Graphical Vim), then I was able to edit Markdown files with embedded
console sessions with the same syntax highlighting as in the final document.

When the appropriate configuration files are in place then any text file
named with a *.console* filename extension written in console-consistent
format will be syntax-highlighted with these editors:

   * a Vim-based editor
   * a KDE Kate editor

This repository contains the needed configuration files.

I have not looked at syntax highlighting console sessions yet in editors
like gedit, pluma or emacs.

## *Console* is not a language

Most syntax highlighting is based on highlighting the specific syntax
of various computer languages.  'Console' is instead a contrived set of syntax 
requirements to represent console input/output for Linux and UNIX-based
command line sessions.

The *test.console* file in this repository can be used to test whether
your local configuration works.  It also explains the simple syntax 
requirements which invoke the highlighter.

## Where to install files for Gvim/Vim

For the Gvim or Vim editors, the Vim files should be installed in
your home directory:

```console
// Change directories to your home directory:
$ cd

// Make the necessary subdirectories:
$ mkdir -p .vim/syntax .vim/ftdetect

// Copy the files into place:
$ cp /path/to/vim.syntax ~/.vim/syntax/console.vim
$ cp /path/to/vim.ftdetect ~/.vim/ftdetect/console.vim
```

To have the same console syntax highlighting embedded in Markdown files
then enable the console syntax in your *.vimrc* file by copying the 
settings in *vimrc.example*.

```console
// Create the file if it does not exist; otherwise edit the file.  Add
//  the 'fenced languages' stanza:
$ vim ~/.vimrc
$ grep fenced_languages ~/.vimrc
let g:markdown_fenced_languages = ['console']
```

## Where to install files for Kate

For the Kate editor, it will depend on the version of Kate you are using.
In my case on Ubuntu LTS 22.04 the console.xml file is installed this way:

```console
// Change directories to your home directory:
$ cd

// Make the necessary subdirectory and copy the XML file there:
$ mkdir -p .local/share/katepart5/syntax
$ cp /path/to/console.xml ~/.local/share/katepart5/syntax/
```

To have the same console syntax highlighting embedded in Markdown files
then it is a bit more complicated than the *Vim* example.  You need to
copy the current XML syntax file from Kate, and add a few lines to enable
fenced 'console' code blocks.  I made it work by adding the lines just above
the settings for *bash* in two places:

```console
$ cd ~/.local/share/katepart5/syntax/
// wget the file, or just browse to this link and copy/paste it:
$ wget -N -nd \
https://raw.githubusercontent.com/jgm/skylighting/master/skylighting-core/xml/markdown.xml

// Keep a copy of the original file:
$ cp -p markdown.xml markdown.xml.orig
$ kate markdown.xml
```

The lines to add are these:

```
<!-- just before first bash-code add this: -->
 <RegExpr attribute="Fenced Code" context="#pop!console-code"
  String="&fcode;\s*(?:console)&end;" insensitive="true"
  beginRegion="code-block"/>

<!-- just before second bash-code add this -->
 <context attribute="Normal Text" lineEndContext="#stay" name="console-code">
     <IncludeRules context="code"/>
     <IncludeRules context="##console" includeAttrib="true"/>
 </context>

```

[home-server]: https://github.com/deatrich/linux-home-server/
[doc-with-pandoc-md]: https://github.com/deatrich/doc-with-pandoc-markdown/
[kde-syntax-hi]: https://github.com/KDE/syntax-highlighting/tree/master
[kate]: https://kate-editor.org/
