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

   `reStructuredText`_ (reST) is primarily used in Python community for writing
   technical documentation, both Python docstrings and standalone documents.

   Unlike `Markdown`_, reST covers officially many advanced markup, for example
   metadata, automatic table of contents, tables and semantic text. It has also
   a standardized way for writing custom extensions.

   reST is commonly used with `Sphinx`_, which is a documentation generator
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
.. _Markdown: https://daringfireball.net/projects/markdown/
.. _Python documentation: https://docs.python.org
.. _reStructuredText: http://docutils.sourceforge.net/rst.html
.. _Sphinx: http://www.sphinx-doc.org

Markup
=======

Sections
--------

Sections headers are a single line of text with an underline or an underline
and an overline of non-alphanumeric characters (adornment), which are at least
as long as the text:

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

* ``#`` with overline and centered title text using 2 spaces at the left
  edge, for parts (H1 in a master document in Sphinx) [#]_

  .. code:: rst

     #########
       Title
     #########

* ``*`` with overline, for chapters (H1 in a common document)

  .. code:: rst

     *****
     Title
     *****

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
recommended by reST:

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

   There may exist a reST plugin to your editor, which can speed up creating
   section headers by highlighting a section title and applying a keyboard
   shortcut for a specific heading level.

.. _The Python documentation: https://devguide.python.org/documenting/#sections

Paragraphs
----------

Paragraphs are chunks of text aligned at the left edge and separated by a blank
line:

.. code:: rst

   This is a paragraph over
   three lines, but the line breaks will not be preserved after
   transforming reST documents to other text formats as HTML or PDF.

   This is another paragraph.

To preserve line breaks in paragraphs, a vertical bar ("|") with a space must
be used at the left edge of each line with a line break in order to create
line blocks:

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
   special cases (tables, links, code samples), when it is allowed to exceed
   this limit.

Text styles
-----------

Text in paragraphs and other body elements [#]_ is normal by default (no text
style), unless some parts of text need to be emphasized. One asterisk ("*")
around a word(s) indicates emphasis (italics), whereas two asterisks indicate
strong emphasis (boldface):

.. code:: rst

   *This part of text will be rendered in italics*,
   **while this one in bold**.

reST is pretty smart when to not use italics or boldface, if there are spaces
or asterisks inside a word:

.. code:: rst

   1 * 1 is 1. 2*2 is 4. 3 ** 3 is 27.

However, if there is a need to emphasis characters inside a word, then around
asterisks must be spaces escaped:

.. code:: rst

   thisis\ **one**\ word (thisisoneword with "one" in bold)

Escaping can be also used with asterisks or any other special markup found
later in this book:

.. code:: rst

   Explicitly: \*italics\* (twice)
   Implicitly: \**bold** (once)

Besides emphasis, text may be monospaced, which is used for inline code
samples. Each character inside double backquotes ("``") is preserved:

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

Definitions lists consists of a term and a definition for that term starting
at the next line with indentation and separated by a blank line from other
terms:

.. code:: rst

   reST
      A shortcut for reStructuredText markup language.

   HTML
      Hypertext Markup Language for creating web pages.

Definitions may contain more than one paragraph or other body elements:

.. code:: rst

   Term
      This term cannot be *briefly* explained.

      It requires **two** paragraphs for its definition.

.. tip::

   The Python documentation uses 3 spaces for indentation in reST documents
   (mainly due to Directives, described later in his book).

Field Lists
^^^^^^^^^^^

Field lists are actually two-column tables, where each row has a header (field)
in the first column and content (field body) in the second column:

.. code:: rst

   :Shortcut: reST
   :Filename extension: ``.rst``
   :Reference documentation: www

Field bodies may contain more than one paragraph or other body elements:

.. code:: rst

   :Body elements:
      * paragraphs
      * lists

      etc.

Option Lists
^^^^^^^^^^^^

Option lists are two-column tables, where each row has an option(s) in the
first column and description for that option in the second column separated by
at least two spaces:

.. code:: rst

   -v               Verbose
   -h, --help       Display help message
                    and exit
   -n number        Provide a number
   -h, --host=host  Host to connect

.. note::

   If reST is used inside Sphinx, then it is better to use Sphinx's directives
   for documenting CLI programs and options (no need to control spaces, better
   rendering in other formats, easy to manage).

.. tip::

   There may exist a reST plugin to your editor which support automatic
   alignment in option lists by highlighting an option list and applying a
   keyboard shortcut.

Horizontal Lines
----------------

Horizontal lines are at least four same successive punctuation characters
surrounded by blank lines between paragraphs:

.. code:: rst

   This is a paragraph.

   ----

   This is another paragraph.

The Python documentation has no convention for the horizontal lines. Propably
they do not use them at all. However, the documentation for reST uses hyphens in
all examples.

.. note::

   The purpose of horizontal lines is to signal a change in a subject between
   paragraphs in literature. In reST documents, the horizontal lines are rather
   used at the end of files with footnotes.

   If your editor allows you to quickly insert 80 hyphens at once, then you may
   use them instead of four hyphens:

   .. code:: rst

      ...

      --------------------------------------------------------------------------------

      .. [#] Footnote A
      .. [#] Footnote B
      .. [#] Footnote C

Directives
==========

Interpreted Text Roles
======================

References
==========

* `Python Developer's Guide - Documenting Python`__
* `reStructuredText`__
* `Sphinx - Getting Started`__
* `Sphinx - reStructuredText Primer`__
* `Wikipedia - reStructuredText`__

__ https://devguide.python.org/documenting/
__ reStructuredText_
__ https://www.sphinx-doc.org/en/master/usage/quickstart.html
__ http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html
__ https://en.wikipedia.org/wiki/ReStructuredText

--------------------------------------------------------------------------------

.. rubric:: Footnotes

.. [#] Special ``index.rst`` files which serves as a welcoming page with a table
   of contents.
.. [#] Body elements are markup inside sections (paragraphs, lists, tables
   etc.).
