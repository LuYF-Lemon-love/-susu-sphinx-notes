012 First steps to document your project using Sphinx
=====================================================

源教程地址: https://www.sphinx-doc.org/en/master/tutorial/first-steps.html .

Building your HTML documentation
--------------------------------

The index.rst file that sphinx-quickstart created has some content already, 
and it gets rendered as the front page of your HTML documentation. 
It is written in reStructuredText, a powerful markup language.

Modify the file as follows:

**docs/source/index.rst**

::

 Welcome to Lumache's documentation!
 ===================================
 
 **Lumache** (/lu'make/) is a Python library for cooks and food lovers that
 creates recipes mixing random ingredients.  It pulls data from the `Open Food
 Facts database <https://world.openfoodfacts.org/>`_ and offers a *simple* and
 *intuitive* API.
 
 .. note::
 
    This project is under active development.

.. note::

   This project is under active development.

This showcases several features of the reStructuredText syntax, including:

- a section header using ``===`` for the underline,

- two examples of Inline markup: ``**strong emphasis**`` (typically bold) and ``*emphasis*`` (typically italics),

- an inline external link,

- and a note admonition (one of the available directives)

Now to render it with the new content, 
you can use the sphinx-build command as before, 
or leverage the convenience script as follows:

.. prompt:: bash $,(.venv)...$ auto

   (.venv)...$ cd docs
   (.venv)...$ make html

After running this command, you will see that index.html reflects the new changes!

Building your documentation in other formats
--------------------------------------------

Sphinx supports a variety of formats apart from HTML, 
including PDF, EPUB, and more. 
For example, to build your documentation in EPUB format, 
run this command from the docs directory:

.. prompt:: bash $,(.venv)...$ auto

   (.venv)...$ make epub

After that, you will see the files corresponding to the e-book under docs/build/epub/. 
You can either open Lumache.epub with an EPUB-compatible e-book viewer, 
like Calibre, or preview index.xhtml on a web browser.

.. note::

   To quickly display a complete list of possible output formats, 
   plus some extra useful commands, you can run ``make help``.

Each output format has some specific configuration options that you can tune, 
including EPUB. For instance, the default value of epub_show_urls is inline, 
which means that, by default, URLs are shown right after the corresponding link, 
in parentheses. 
You can change that behavior by adding the following code at the end of your ``conf.py``:

::

 # EPUB options
 epub_show_urls = 'footnote'

With this configuration value, and after running make epub again, 
you will notice that URLs appear now as footnotes, 
which avoids cluttering the text. Sweet! Read on to explore other ways to customize Sphinx.

.. note::

   Generating a PDF using Sphinx can be done running make latexpdf, 
   provided that the system has a working LaTeX installation, 
   as explained in the documentation of sphinx.builders.latex.LaTeXBuilder. 
   Although this is perfectly feasible, such installations are often big, 
   and in general LaTeX requires careful configuration in some cases, 
   so PDF generation is out of scope for this tutorial.