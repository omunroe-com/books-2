==================
 reStructuredText
==================
-----------------------------
 Lightweight markup language
-----------------------------

:Author: `Davie Badger`_
:Contact: davie.badger@gmail.com
:Copyright: `Creative Commons Attribution 4.0 International Public License`_

:Abstract:
   `reStructuredText`_ (RST or also reST) is primarily used in Python community
   for writing technical documentation, both Python docstrings and standalone
   documents.

   Unlike `Markdown`_, |RST| covers officially many advanced markup, for example
   document metadata, automatic table of contents, tables and semantic text. It
   has also a standardized way for writing custom extensions (directives and
   interpreted text roles) via `Docutils`_ library written in Python.

   |RST| is commonly used with `Sphinx`_, which is a documentation generator
   originally developed for the official `Python documentation`_, but now it is
   independent from projects using a different programming language or none at
   all.

   :Filename extension: ``.rst``
   :Reference documentation: http://docutils.sourceforge.net/rst.html#reference-documentation

.. contents::

.. sectnum::
   :depth: 3
   :suffix: .

.. _Creative Commons Attribution 4.0 International Public License: https://creativecommons.org/licenses/by/4.0/
.. _Davie Badger: https://github.com/daviebadger
.. _Docutils: http://docutils.sourceforge.net/
.. _Markdown: https://daringfireball.net/projects/markdown/
.. _Python documentation: https://docs.python.org
.. _reStructuredText: http://docutils.sourceforge.net/rst.html
.. _Sphinx: http://www.sphinx-doc.org

Markup
======

Markup is a set of special characters within text. Parsers thanks to them know,
how to transform the given text in a document to other text or file formats, for
example HTML or PDF.

Sections
--------

Sections headers are a single line of text with an underline or an underline and
an overline of non-alphanumeric characters (adornment), which are at least as
long as the text:

.. code:: rst

   *************
   Section Title
   *************

   ...

Although there are many non-alphanumeric characters, none of them is associated
with a specific heading level. Therefore, it is very important to be consistent
with heading levels through a document.

The Python documentation has the following convention (with analogous heading
levels in HTML), which may be followed:

* ``#`` with overline and centered title text using 2 spaces at the left edge,
  for parts (H1 in master documents in Sphinx) [#]_

  .. code:: rst

     ##################
       Document Title
     ##################

* ``*`` with overline, for chapters (H1 in ordinary documents)

  .. code:: rst

     **************
     Document Title
     **************

* ``=`` for sections (H2)

  .. code:: rst

     Section Title
     =============

* ``-`` for subsections (H3)

  .. code:: rst

     Subsection Title
     ----------------

* ``^`` for subsubsections (H4)

  .. code:: rst

     Subsubsection Title
     ^^^^^^^^^^^^^^^^^^^

* ``"`` for paragraphs (H5)

  .. code:: rst

     Paragraph Title
     """""""""""""""

For standalone documents out of documentation, if there is a need to use a
document title with a subtitle, then the following adornment style is
recommended by |RST|:

.. code:: rst

   ================
    Document Title
   ================
   ----------
    Subtitle
   ----------

   Section Title
   =============

   ...

.. tip::

   There may exist a |RST| plugin to your editor, which can speed up creating
   section headers by highlighting a section title and applying a keyboard
   shortcut for a specific heading level.

.. _The Python documentation: https://devguide.python.org/documenting/#sections

Paragraphs
----------

Paragraphs are chunks of text aligned at the left edge and separated by a blank
line:

.. code:: rst

   This is a paragraph over
   three lines, but the line breaks
   will not be preserved.

   This is another paragraph.

To preserve line breaks in paragraphs, a vertical bar ("|") with a space must be
used at the left edge of each line with a line break in order to create line
blocks:

.. code:: rst

   | First line
   | Second line
   | Third line
   |
   | Fifth line

   ...

It is also possible to join lines if they are left-aligned with text at a line
containing a line break:

.. code:: rst

   | A really long line
     which continues over
     another lines

   ...

.. tip::

   The Python documentation uses maximally 80 characters per line except a few
   special cases (tables, hyperlinks, code samples), when it is allowed to
   exceed this limit.

Text styles
-----------

Text in paragraphs and other body elements [#]_ is normal by default (no text
style), unless some parts of text need to be emphasized. One asterisk ("*")
around a word(s) indicates emphasis (italics), whereas two asterisks indicate
strong emphasis (boldface):

.. code:: rst

   *This part of text will be rendered in italics*,
   **while this one in bold**.

|RST| is pretty smart when to not use italics or boldface, if there are spaces
or asterisks inside a word:

.. code:: rst

   1 * 1 is 1. 2*2 is 4. 3 ** 3 is 27.

However, if there is a need to emphasis characters inside a word, then around
asterisks must be spaces escaped:

.. code:: rst

   thisis\ **one**\ word (thisisoneword with "one" in bold)

Escaping can be also used with asterisks or any other special markup found later
in this book:

.. code:: rst

   Explicitly: \*italics\* (twice)
   Implicitly: \**bold** (once)

Besides emphasis, text may be monospaced, which is used for inline code samples.
Each character inside double backquotes ("``") is preserved:

.. code:: rst

   To emphesasize text, you need to use ``*`` around a word, e.g. ``*italics*``.

.. note::

   Because both emphasis and strong emphasis use asterisks, it is not possible
   to use italics and boldface at the same time.

Lists
-----

Bulleted Lists
^^^^^^^^^^^^^^

Bulleted lists consists of a bullet point character, usually an asterisk (like
in the Python documentation) followed by one space and an item:

.. code:: rst

   * first item
   * second item
   * third item

Items may continue on the next lines like pagraphs with line breaks or have
other body elements inside text:

.. code:: rst

   * first item over
     two lines
   * second item with two paragraphs

     This is the **second** pagagraph.

Bulleted lists may be also nested, if the inner lists are surrounded by blank
lines and left-aligned with text at the previous line:

.. code:: rst

   * first item
     over two lines

     * first subitem

       * first subsubitem

     * second subitem
     * third subitem

   * second item

Numbered Lists
^^^^^^^^^^^^^^

Numbered (enumerated) lists consists of a number and a formatting type, usually
a period (like in the Python documentation) followed by one space and an item:

.. code:: rst

   1. first item
   2. second item over
      two lines
   3. third item

Items may be automatically numbered for greater convenience:

.. code:: rst

   #. item
   #. item
   #. item

Both bulleted and enumerated lists may be combined:

.. code:: rst

   * first outer bulleted item

     1. first numbered item

        * first inner bulleted item

     2. second numbered item

   * second outer bulleted item
   * third outer bulleted item

Definition Lists
^^^^^^^^^^^^^^^^

Definitions lists consists of a term and a definition for that term starting at
the next line with indentation and separated by a blank line from other terms:

.. code:: rst

   RST
      A shortcut for reStructuredText markup language.

   HTML
      Hypertext Markup Language for creating web pages.

Definitions may contain more than one paragraph or other body elements:

.. code:: rst

   Term
      This term cannot be *briefly* explained.

      It requires **two** paragraphs for its definition.

.. tip::

   The Python documentation uses 3 spaces for indentation in |RST| documents
   (mainly due to Directives, described later in his book).

Field Lists
^^^^^^^^^^^

Field lists are actually two-column tables, where each row has a header (field)
in the first column and content (field body) in the second column:

.. code:: rst

   :Shortcut: RST or reST
   :Filename extension: ``.rst``
   :Reference documentation: www

Field bodies may contain more than one paragraph or other body elements:

.. code:: rst

   :Body elements:
      * paragraphs
      * lists

      etc.

.. note::

   If a field list is used right after a document title or a subtitle, then
   the field list is supposed to be a bibliographic field list (metadata about
   the document):

   .. code:: rst

      **************
      Document Title
      **************

      :Author: Davie Badger

   Tbere are special bibliographic fields, which are rendered differently than
   other fields:

   * ``:Abstract:`` - body elements are allowed
   * ``:Address:`` - a multi-line address with preserved newlines
   * ``:Author:``
   * ``:Authors:`` - a bulleted list of authors
   * ``:Contact:``
   * ``:Copyright:``
   * ``:Date:``
   * ``:Dedication:`` - body elements are allowed
   * ``:Organization:``
   * ``:Status:``
   * ``:Version:``

Option Lists
^^^^^^^^^^^^

Option lists are two-column tables, where each row has an option(s) in the first
column and a description for that option in the second column which is separated
by at least two spaces:

.. code:: rst

   -v               Verbose
   -h, --help       Display help message
                    and exit
   -n number        Provide a number
   -h, --host=host  Host to connect

It is possible to use body elements in descriptions, but they must be
left-aligned with the previous lines. The longer options, the more indentations
is needed for the body elements on the next lines:

.. code:: rst

   -n number  Provide a number.

              Allowed formats:

              * integer
              * float

.. note::

   If |RST| documents are written inside Sphinx, then it is better to use its
   directives for documenting command-line programs and options, because they
   more scalable, easier to maintain and better rendered in other text formats.

.. tip::

   There may exist a |RST| plugin to your editor which support automatic
   alignment in option lists by highlighting an option list and applying a
   keyboard shortcut.

Hyperlinks
----------

Hyperlinks point to internal or external location. The most easiest way to
create a hyperlink target is to place an URI into text:

.. code:: rst

   The Python documentation is located on https://docs.python.org/.

Alternatively, URIs may be embedded (surrounded by angle brackets "<>") within
a hyperlink text inside backquotes (also backticks "`") followed by an
underscore:

.. code:: rst

   The Python documentation is `HERE <https://docs.python.org/>`_.

Nevertheless, in |RST| philosophy, hyperlink targets should be placed away of
text due to readability. Possible places are the end of a section or a whole
document. Hyperlinks within text should reference to these targets.

Hyperlink references may be single words followed by an underscore or several
words inside backqoutes also followed by an underscore, which are associated
with hyperlink targets leading to URIs:

.. code:: rst

   Python_ has `official documentation`_

   .. _Python: https://www.python.org/
   .. _official documentation: https://docs.python.org/

Within hyperlink targets it is possible to group several targets and point to
single location or point from one hyperlink target to another hyperlink
reference:

.. code:: rst

   Python_, `Python 3`_, `Python 3.7`_, all point to the same location_.

   .. _Python:
   .. _Python 3:
   .. _Python 3.7: https://www.python.org/
   .. _location: Python_

Hyperlinks can be anonymous (not named), which may be handy in cases when same
hyperlink text need to target two different locations. They may be also used in
a list with hyperlinks. Anonymous hyperlinks require two trailing underscores:

.. code:: rst

   References
   ==========

   * link__
   * `long link`__

   .. __: www for link
   .. __: www for long link

The anonymous hyperlink targets may be shortened:

.. code:: rst

   References
   ==========

   * link__
   * `long link`__

   __ www for link
   __ www for long link

.. note::

   If hyperlink references contain colons, then they must be escaped or
   backquoted within hyperlink targets:

   .. code:: rst

      `Link: with colon`_ or `Another link: with colon`_

      .. _`Link: with colon`: ...
      .. _Another link\: with colon: ...

.. tip::

   Sections in documents may be also hyperlinked according to their titles:

   .. code:: rst

      Section A
      =========

      See `Section B`_ below.

      Section B
      =========

   Other body elements may be also hyperlinked, if they have an internal
   hyperlink reference in the prior paragraph:

   .. code:: rst

      .. _List of shortcuts:

      * rst / RST
      * reST

      reST has a few shortcuts, see `List of shortcuts`_ (above).

Tables
------

Simple Tables
^^^^^^^^^^^^^

Simple tables are tables without row or column spans (only in headers), in which
are equal signs ("=") used as an adornment style for table headers and for
ending a table. Each column must be separated by two spaces:

.. code:: rst

   This is a simple table:

   =========  ========  ======  ===
   Firstname  Lastname  Gender  Age
   =========  ========  ======  ===
   Davie      Badger    Male    24
   Jacob      Badger    Male    19
   =========  ========  ======  ===

All columns except the last one must be adorned as long as the widest cell in
that column. Within these long columns, table headers may be centered:

.. code:: rst

   =======  =======  ===
      A        B      C
   =======  =======  ===
   Value A  Value X  Value 1
   Value B  Value Y  Value 2
   Value C  Value Z  Value 3
   =======  =======  ===

.. note::

   Although simple tables enable to use column spans in table headers or empty
   cells via single backward slash ("\") in that cells, it is better to use
   `Grid Tables`_ for these features and leave simple tables to be just simple
   tables.

.. tip::

   There may exist a |RST| plugin to your editor, which can speed up modifying
   simple tables by highlighting a table and applying a keyboard shortcut for
   extending / shortering adornment and realigning text within that table.

Grid Tables
^^^^^^^^^^^

Grid tables are tables with full suport for row spans, column spans, empty cells
and body elements inside cells. However, these features come at cost, because
grid tables are really cumbersome to design without a |RST| plugin in an editor.

Grid tables consists of plus signs ("+") as corners, vertical bars ("|") as
column separators, minus signs ("-") as row separators and equal signs ("=") as
separator between table headers and other rows:

.. code:: rst

   This is a grid table:

   +------------+--------------------+----------+
   | Header A   | Header B           | Header C |
   +============+====================+==========+
   | A1         | B1 + C1 (column span)         |
   +------------+--------------------+----------+
   | A2 + A3    | * first item       | C2       |
   | (row span) | * second item      |          |
   |            | * third item       |          |
   |            +--------------------+----------+
   |            | C3 is **empty**    |          |
   +------------+--------------------+----------+

.. note::

   If vertical bars are used inside cells, for example in inline code samples,
   then it is really important, where are the vertical bars located in that
   cells.

   |RST| may be confused, if a vertical bar is placed right in a place, which
   indicates column separation. Therefore a blank line on the next line is
   needed in this case to signal |RST| that the vertical bar has a different
   purpose:

   .. code:: rst

      +--------------+----------+-----------+-----------+
      | row 1, col 1 | column 2 | column 3  | column 4  |
      +--------------+----------+-----------+-----------+
      | row 2        | Use the command ``ls | more``.   |
      |              |                                  |
      +--------------+----------+-----------+-----------+
      | row 3        |          |           |           |
      +--------------+----------+-----------+-----------+

.. tip::

   |RST| provides directives for simplier work with tables, which will be
   covered later in this book.

Code Samples
------------

Code samples are indented pieces of code, which begin with a special unindented
paragraph containing only two colons followed by a blank line:

.. code:: rst

   Example from Python:

   ::

      def hello(name="World"):
          print(f"Hello {name}")


      hello()
      hello("Davie")

The two colons may appear at the end of text followed by a space:

.. code:: rst

   Example from Python: ::

      hello()

Both previous examples may be even further shortened, when |RST| will left one
colon instead of two colons at the end of the paragraph which will look exactly
like in the first example:

.. code:: rst

   Example from Python::

      hello()

Short Python code samples without blank lines may be also written like
interactive interpreter (no need to indent code):

.. code:: rst

   Example from Python:

   >>> print("Hello World")
   Hello World

.. note::

   Code samples using ``::`` markup are not highlighted at all, except the
   Python interactive examples. There are special directives for this case
   (either in |RST| or Sphinx).

Block Quotes
------------

Block quotes are just indented paragraphs, which may be nested, if text is
left-aligned with the previous lines and the indentations are keeped:

.. code:: rst

   This is a ordinary paragraph.

      This is a **quoted** paragraph.

         This is a *nested* quoted paragraph.

      This is another quoted paragraph
      over two lines.

Several block quotes may be separated from each other either by another ordinary
paragraphs or using two periods as a separator (empty comment):

.. code:: rst

   Famoues quotes from X Y:

      First quote.

   ..

      Second quote.

   ..

      Third quote.

At the end of block quotes, it is possible to give attribution to a specific
author of that quotes, if before name are two hyphens:

.. code:: rst

   This is a ordinary paragraph.

      This is a super quote.

      -- X Y

Comments
--------

Comments are hidden pagraphs, which starts with two periods followed by a space
and other lines are left-aligned to this indentation:

.. code:: rst

   .. This is a comment
      over two lines.

      This is another paragraph inside this single comment.

Footnotes
---------

Footnotes consits of numbers (indexes) inside square brackets followed by an
underscore in text and descriptions (footnote) for that indexes usually at the
end of documents:

.. code:: rst

   ``#`` with overline is used as an adornment style for document titles in
   master documents in Sphinx [1]_.

   .. [1] Master documents are special ``index.rst`` files with a TOC.

For short documents may be explicit numbers enough, but if a document is long or
regularly changed, it is better to use auto-numbered footnotes to save time with
overriding:

.. code:: rst

   ``#`` with overline is used as an adornment style for document titles in
   master documents in Sphinx [#]_.

   .. [#] Master documents are special ``index.rst`` files with a TOC.

Long footnotes may continue on another lines with other body elements if they
are left-aligned with the left square bracket:

.. code:: rst

   .. [#] Master documents are special ``index.rst``
      files with a TOC.

      They are stored in each directory (group of documents).

.. note::

   Each footnote is automatically hyperlinked to itself. It is possible in
   rendered |RST| documents to click on an index in text, see a footnote at the
   end of a document, click on the index next to the footnote and be back in
   text where I had been previously.

.. tip::

   To insert another footnote between existing auto-numebered footnotes requires
   only to find a previous or next occurence of ``[#]_`` to know where to
   properly place the new footnote.

Horizontal Lines
----------------

Horizontal lines are at least four same successive punctuation characters
surrounded by blank lines between paragraphs:

.. code:: rst

   This is a paragraph.

   ----

   This is another paragraph.

The Python documentation has no convention for the horizontal lines. Propably
they are not used at all. However, the documentation for |RST| uses hyphens in
all examples.

.. note::

   The purpose of horizontal lines is to signal a change in a subject between
   paragraphs in literature. In |RST| documents, the horizontal lines are rather
   used at the end of files with footnotes.

   If your editor allows you to quickly insert 80 hyphens at once, then you may
   use them instead of four hyphens:

   .. code:: rst

      ...

      --------------------------------------------------------------------------------

      .. [#] Footnote A
      .. [#] Footnote B
      .. [#] Footnote C

Substitution
------------

Substitions are words inside vertical bars ("|"), which will be during rendering
substituted with other words according to the given inline directive, which was
used, e.g. a directive for replacing text:

.. code:: rst

   |RST| is really long to type, so it is better to use a shorcut via
   substitutions.

   Also |PY 3| is mentioned a lot of times within a document, so it is better to
   replace it with a specific version.

   .. |RST| replace:: reStructuredText
   .. |PY 3| replace:: Python 3.7.

Other possible inline directives and directives in general are covered in the
`Directives`_ section.

.. tip::

   Substitutions may be combined with hyperlinks:

   .. code:: rst

      |RST|_ is really long to type, so it is better to use a shorcut via
      substitutions.

      .. |RST| replace:: reStructuredText
      .. _RST: http://docutils.sourceforge.net/rst.html

Directives
==========

Roles
-----

Directives for manipulating `Interpreted Text Roles`_.

default-role
^^^^^^^^^^^^

role
^^^^

Interpreted Text Roles
======================

Interpreted text roles are pieces of text surrounded by single backquotes ("`")
and implicitly or explicitly prefixed with a role, which could mean a special
text style or a shortcut instead of a hyperlink, and with spaces around (may be
escaped):

.. code:: rst

   * this is special `interpreted text` without a role (implicit, using the default)
   * thisis\ `one`\ word (thisisoneword with interpreted "one" word)

The default role is `:title-reference:` (also `:title:`), which is intended to
be use as a title of a book or any other text materials:

.. code:: rst

   * `Super Title` is a book from X (implicit)
   * :title:`Another Super Title` is also a book from X (explicit)

.. note::

   The default role may be changed via `default-role`_ directive, however it is
   better to use always explicit roles.

PEP
---

Create a link to a specific `PEP`_ (Python Enhancement Proposal):

.. code:: rst

   See :PEP:`8` for Python style guide.

.. _PEP: https://www.python.org/dev/peps/

RFC
---

Create a link to a specific `RFC`_ (Request For Comments):

.. code:: rst

   See :RFC:`3339` for standard date and time formats.

.. _RFC: https://tools.ietf.org/rfc/index

Glossary
========

|RST| uses officially the following terminology for markup syntax:

Citations
   `Footnotes`_ with alphanumeric characters plus hyphens, underscores and
   periods instead of numbered indexes, e.g. ``[label123]_``.

   Citations are rarely used, footnotes are much more prefered.
Doctest Blocks
   `Code Samples`_ with interactive Python interpreter.
Inline Markup
   `Text Styles`_ plus markup inside paragraphs, like `Hyperlinks`_,
   `Footnotes`_ and `Substituion`_ without parts inside ``..`` constructs.
Literal Blocks
   `Code Samples`_
Transitions
   `Horizontal Lines`_

References
==========

* `Python Developer's Guide - Documenting Python`__
* `reStructuredText`__
* `reStructuredText - Markup Specification`__
* `Sphinx - Getting Started`__
* `Sphinx - reStructuredText Primer`__
* `Wikipedia - reStructuredText`__

__ https://devguide.python.org/documenting/
__ reStructuredText_
__ http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html
__ https://www.sphinx-doc.org/en/master/usage/quickstart.html
__ http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html
__ https://en.wikipedia.org/wiki/ReStructuredText

--------------------------------------------------------------------------------

.. rubric:: Footnotes

.. [#] Special ``index.rst`` files which serves as a welcoming page with a table
   of contents.
.. [#] Body elements are markup inside sections (paragraphs, lists, tables
   etc.).

.. |RST| replace:: reStructuredText
