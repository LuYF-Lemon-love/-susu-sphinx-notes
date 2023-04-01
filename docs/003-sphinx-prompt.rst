003 sphinx-prompt
=================

源教程地址: https://pypi.org/project/sphinx-prompt/ .

Install
-------

.. prompt:: bash $

    pip install sphinx-prompt

Initialize
----------

In ``conf.py`` add ``extensions += ['sphinx-prompt']``.

Syntax
------

A default prompt can be created using a ``prompt`` directive:

::

 .. prompt::

    <statements>

The prompt can be further customized in one of two ways:

- Using positional arguments:

::

 .. prompt:: [<language> [<prompts> [<modifiers>]]]

    <statements>

- Using options:

 .. prompt::
     :language: <language>
     :prompts: <prompts>
     :modifiers: <modifiers>

    <statements>

While these constructs generate the same output, the positional arguments cannot be used if you want to use a prompt that contains spaces. This is a limitation of reStructuredText.

Positional arguments can be mixed with options if they don’t overlap (so if you pass prompts using options, you can only pass the language using positional arguments):

::

 .. prompt:: bash
     :prompts: (cool_project) $

    python3 -m pip install --upgrade sphinx-prompt

Language
--------

Supported language:

- ``text`` (no pigments, default)

- ``bash``

- ``batch``

- ``powershell``

- ``python``

- ``scala``

Prompt(s)
---------

If modifier is auto, a comma-separated list of prompts to find in the statements.

Else the prompt to add on each statements, for Python and Bash language the end ``\`` is supported.

Defaults to empty, except for the shell languages listed below:

- ``bash`` - ``$``

- ``batch`` - ``C:\>``

- ``powershell`` - ``PS C:\>``

Examples
--------

.. seealso:: See: `Sphinx-prompt <http://sbrunner.github.io/sphinx-prompt/>`_ .

1. 

::

 .. prompt:: bash

     cd <folder>
     cp <src> \
         <dst>
     cd -

Results:

.. prompt:: bash

    cd <folder>
    cp <src> \
        <dst>
    cd -
        
2. 

::

 .. prompt:: bash #

     cd 
     cd -

Results:

.. prompt:: bash #

    cd 
    cd -

3. 

::

 .. prompt:: bash $,# auto

     $ sudo
     # exit
     $
              
Results:

.. prompt:: bash $,# auto

    $ sudo
    # exit
    $
       
4. 

::

 .. prompt:: bash $,(env)...$ auto

     $ source env/bin/activate
     (env)...$ deactivate
     $

Results:

.. prompt:: bash $,(env)...$ auto

    $ source env/bin/activate
    (env)...$ deactivate
    $

Run tests and prospector
------------------------

::

 python3 -m pip install --user --upgrade poetry
 poetry install
 poetry run pytest
 poetry run prospector

The code should be formatted with ``black`` add ``isort``.

Create new release
------------------

::

 git tag <version>
 git push origin <version>