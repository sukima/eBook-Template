Template for Writing an eBook
=============================

This project contains a template used to write eBooks using
[AsciiDoc][1].

This a fork of [akosmasoftware's eBook-Template][2].

The aim of the project is to provide a boilerplate used to generate
eBooks in several formats on one operation:

- Self-contained HTML
- ePub
- PDF

Motivation
----------

Why using such a complex setup instead of just using a simpler tool like
Word or Pages?

- The primary motivation of this template is versioning. Being able to
  use plain text files as input for the book brings the possibility of
  versioning each change individually using Git, Subversion or any other
  similar tool. This also opens up the door to collaboration among team
  members when editing a document.
- The second motivation is to separate the presentation and the layout
  of the final book from its contents. Other output file types could be
  added in the future.
- This also brings the possibility of using any text editor in just
  about any operating system; files are just plain text files that can
  be edited with gEdit, Notepad, Emacs, Vim, TextEdit, or any other
  tool.
- Markup languages like Markdown or Asciidoc (used in this template) are
  simpler and more readable than LaTeX or other SGML-like languages,
  making the files readable and lean even when edited in a text editor
  without any syntax highlighting or formatting support.
- Finally, being able to streamline the creation of the three versions
  of the book in just one command-line operation allows the whole setup
  to be automatized.

How it Works
------------

The `master.asciidoc` file at the root of this project provides the
guiding structure of the book. Chapters can be shuffled around,
independently of their contents or internal structure.

Individual chapters are stored in the `chapters` folder, one file per
chapter.

Images are stored as PNG files in the `images` folder.

The `build.sh` script creates a temporary `_build` folder, copies all
the different elements in it (the master file, the chapters and the
images) and commands the execution of the whole toolchain in order to
get the final result.

Software Requirements
---------------------

Follow these instructions to install the required libraries in Mac OS X:

1. Install [Homebrew][2] if not already installed.
    - If already installed, remember to run `brew update`.
2. Download and install `asciidoc` using Homebrew:
    - `brew install asciidoc`
3. Install source-highlight with Homebrew:
    - `brew install source-highlight`
4. Download and install the latest MacTeX package from
    `http://www.tug.org/mactex/`
5. Install the `dblatex` package manually:
    - `brew install https://raw.github.com/bartschuller/homebrew/master/Library/Formula/dblatex.rb`
6. Download the [kindlegen][3] tool and install it in the following
   path:
    - `/Applications/KindleGen_Mac_i386_v2/kindlegen`

How to build the book 
---------------------

1. Make sure AsciiDoc and dblatex are properly installed.
2. Execute the booklet/build.sh script. This will create the PDF, ePub
   and HTML versions of the book.
3. The script also generates the .mobi (Amazon Kindle) version if the
   [kindlegen][3] tool is installed.

After the build process completes, the compiled eBooks will be available
at the `_build` subfolder.

Troubleshooting
---------------

### PDF build error

If the generation of the PDF fails during "makeindex" follow the
instructions [in this page][5] and add the following line: 

    openout_any = r

to the file `/usr/local/texlive/2011/texmf.cnf`

### EPUB build error

If the EPUB generation causes problems, [check this page][4].

### Installing dblatex

dblatex has to be installed using a custom Homebrew formula, because the
default installation does not include it at the time of this writing.
This might change in the future.

On Ubuntu you must install the `asciidoc` package which includes
`dblatex` and the missing `tex-gyre` package.

### Why not generating the HTML using a2x?

Using a2x for the HTML creation has the following drawbacks:

- It takes longer;
- It does not embed the images in the HTML;
- It does not do syntax highlighting.

However, it creates an index when required.

License
-------

This work is placed in the public domain. It belongs to mankind and to
nobody in particular. Use it to write poetry, arts, science books and
novels. You cannot use it to write hatred or stupid things.

However, just in case, the author does not take any responsibility about
any bad things that might happen when using this template. However, this
should not happen.

Use, share, transform, as much as you want. I hope you find it useful!



[1]: http://www.methods.co.nz/asciidoc/
[2]: https://github.com/akosmasoftware/eBook-Template
[4]: http://francisshanahan.com/index.php/2011/fixing-epub-problem-docbook-xsl-asciidoc-a2x/
[5]: http://hackage.haskell.org/trac/ghc/wiki/Building/MacOSX

