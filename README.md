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
highlighting descriptions are written in XML, using syntax descriptions
designed for KDE's Kate syntax highlighting.

By adding custom Kate syntax highlighting I was able to present console sessions
as fenced code blocks with more interesting syntax highlighting in 
Pandoc-generated Markdown-based documents.

By adding custom Vim syntax highlighting for my favourite editor, Gvim
(Graphical Vim), then I was able to edit Markdown files with embedded
console sessions with the same syntax highlighting as in the final document.

When the appropriate configuration files are in place then any text file
named with a *.console* filename extension written in console-consistent
format will be syntax-highlighted with these editors:

   * a Vim-based editor
   * the KDE Kate editor

This repository contains the needed configuration files.

See the document *using-console-syntax.md* for installation and configuration
details.

[home-server]: https://github.com/deatrich/linux-home-server/
[doc-with-pandoc-md]: https://github.com/deatrich/doc-with-pandoc-markdown/
