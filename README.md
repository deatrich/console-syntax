# Console Syntax Highlighting

While writing a guide using Pandoc Markdown about creating a
[Linux Home Server][home-server] I spent some time understanding issues
and finding solutions.  I then added another guide on
[getting started][doc-with-pandoc-md] with Markdown-based technical guides.

One of the issues I have dealt with is console input/output and 
syntax-highlighting.  When you are helping others understand command line
options it is very useful to **highlight** command line console sessions.

Pandoc uses the Haskell *skylighting* library for syntax highlighting.  The
highlighting descriptions are written in XML, using XML syntax descriptions
[for KDE's Kate syntax highlighting][kde-syntax-hi].

By adding Kate syntax highlighting I was able to present console sessions
as fenced code blocks with more interesting syntax highlighting in 
Markdown editing sessions.

By adding vim syntax highlighting used by my favourite editor, gvim
(Graphical vim), then I was able to edit Markdown files with embedded
console sessions comfortably and quickly.

When the appropriate configuration files are in place then any text file
named with a *.console* filename extension written in console-consistent
format will be syntax-highlighted with these editors:

   * a vim-based editor
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

[home-server]: https://github.com/deatrich/linux-home-server/
[doc-with-pandoc-md]: https://github.com/deatrich/doc-with-pandoc-markdown/
[kde-syntax-hi]: https://github.com/KDE/syntax-highlighting/tree/master
[kate]: https://kate-editor.org/
