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

   Unlike `Markdown`_, reST covers officially many advanced markups, for
   example metadata, automatic table of contents, tables and semantic text. It
   has also a standardized way for writing custom extensions.

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

Markups
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
   section headers by highlighting section titles and applying a keyboard
   shortcut for a specific heading level.

.. _The Python documentation: https://devguide.python.org/documenting/#sections

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

.. rubric:: Footnotes

.. [#] Special ``index.rst`` files which serves as a welcoming page with a
   table of contents.
