======================
Introduction to Sphinx
======================

Philosophy
----------

`Sphinx`_ is what is called a documentation generator.
This means that it takes a bunch of source files in plain text,
and generates a bunch of other awesome things, mainly HTML.
For our use case you can think of it as a program that takes in plain text
files in `reStructuredText`_ format, and outputs HTML.

.. _reStructuredText: http://sphinx-doc.org/rest.html

::

    reST -> Sphinx -> HTML

So as a user of Sphinx, your main job will be writing these text files.
This means that you should be minimally familiar with `reStructuredText`_ as
a language.
It's similar to Markdown in a lot of ways.
It's a lot more powerful than Markdown,
but with that power comes increased
complexity.
Just know that some of the awkward syntax allows you to do more interesting
things further down the line.
In particular, it is extensible: it has a formal way of adding markup
directives that allow more sophisticated parsing. 
For example, Sphinx includes directives to relate documentation of 
modules, classes and methods to the corresponding code.

Installing Sphinx
-----------------

The first step to getting going is installing `Sphinx`_.
Sphinx is a python project, so it can be installed like any other python library.
Several Operating Systems (Mac OS X, Major Versions of Linux/BSD) have Python pre-installed,
so you should just have to run::

    sudo easy_install Sphinx

Instructions for installing Python and Sphinx on Windows can be found at the `Sphinx install page`_.

.. note:: Advanced users can install this in a virtualenv if they wish.
    Also, ``pip install Sphinx`` works fine if you have Pip.


Getting Started
---------------

You'll want to read the `Sphinx Tutorial`_,
as it provides an introduction to a lot of the basic ideas.
For the most part documentation follows a standard structure for our
documentation repository::

    project/
        docs/
            conf.py
            index.rst
            Makefile

We have a top-level ``docs`` directory in the main project directory.
Inside of this is:

``index.rst``:
    This is the index file for the documentation, or what lives at ``/``.
    It normally contains a *Table of Contents* that will link to all other
    pages of the documentation.

``conf.py``: which allows for customization of the output.
    For the most part this shouldn't need to be changed.

``Makefile``: This ships with sphinx,
    and is the main interface for local development,
    but shouldn't be changed.

Other ``*.rst`` files for specific subsections of documentation.

Writing docs
------------

Where you write your documentation will vary based on how the project is
layed out.
Generally major topics will go in an aptly named file in the
top-level docs directory.
If a topic gets larger, it can then be broken out into multiple files in a
directory.
When you write a document, figure out if there is already a place for it in
the project, otherwise feel free to start a new file.

.. warning:: If you make a new file, make sure it is included in the *Table
    of Contents* in ``index.rst``.

reStructuredText
~~~~~~~~~~~~~~~~

To write nice looking documentation you will need to have a basic
understanding of RST as a language.
The `reStructuredText Primer`_ is a great place to start reading, and it
covers most of the syntax you will care about.
The main parts you will need at first are:

* **Inline Markup**
* **Source Code**
* **Hyperlinks**
* **Sections**
* **Directives**

.. note:: You can live-preview RST on the web: http://rst.ninjs.org/
          . Note that it won't understand Sphinx-specific markup though.

Feel free to play around with RST a bit to make sure that you understand how
it works.

.. warning:: RST is white-space sensitive in places.
    If it is acting weirdly, make sure you indent lines that are part of the
    same content similarly.

.. _Sphinx: http://sphinx-doc.org/
.. _headings: http://sphinx.pocoo.org/rest.html#sections
.. _Sphinx Tutorial: http://sphinx-doc.org/tutorial.html#setting-up-the-documentation-sources
.. _reStructuredText Primer:  http://sphinx.pocoo.org/rest.html#rst-primer
.. _Sphinx install page: http://sphinx-doc.org/install.html#windows-install-python-and-sphinx


Building docs
-------------

Once you have your documentation written and want to turn it into HTML,
it's pretty simple. Simply run::

    # Inside top-level docs/ directory.
    make html

This should run Sphinx in your shell, and output HTML.
At the end, it should say something about the documents being ready in
``_build/html``.
You can now open them in your browser by typing::

    open _build/html/index.html

