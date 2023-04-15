016 Automatic documentation generation from code
================================================

源教程地址: https://www.sphinx-doc.org/en/master/tutorial/automatic-doc-generation.html .

In the previous section of the tutorial you manually documented a Python function in Sphinx. 
However, the description was out of sync with the code itself, 
since the function signature was not the same. 
Besides, it would be nice to reuse **Python docstrings** in the documentation, 
rather than having to write the information in two places.

Fortunately, the **autodoc extension** provides this functionality.

Reusing signatures and docstrings with autodoc
----------------------------------------------

To use autodoc, first add it to the list of enabled extensions:

``docs/source/conf.py``

::

 extensions = [
     'sphinx.ext.duration',
     'sphinx.ext.doctest',
     'sphinx.ext.autodoc',
 ]

Next, move the content of the ``.. py:function`` directive to the function docstring 
in the original Python file, as follows:

``lumache.py``

::

 def get_random_ingredients(kind=None):
     """
     Return a list of random ingredients as strings.
 
     :param kind: Optional "kind" of ingredients.
     :type kind: list[str] or None
     :raise lumache.InvalidKindError: If the kind is invalid.
     :return: The ingredients list.
     :rtype: list[str]
 
     """
     return ["shells", "gorgonzola", "parsley"]

Finally, replace the ``.. py:function`` directive from the Sphinx documentation with autofunction:

``docs/source/usage.rst``

::

 you can use the ``lumache.get_random_ingredients()`` function:
 
 .. autofunction:: lumache.get_random_ingredients

If you now build the HTML documentation, 
the output will be the same! With the advantage that it is generated from the code itself. 
Sphinx took the reStructuredText from the docstring and included it, 
also generating proper cross-references.

You can also autogenerate documentation from other objects. 
For example, add the code for the InvalidKindError exception:

``lumache.py``

::

 class InvalidKindError(Exception):
     """Raised if the kind is invalid."""
     pass

And replace the ``.. py:exception`` directive with autoexception as follows:

``docs/source/usage.rst``

::

 or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
 will raise an exception.
 
 .. autoexception:: lumache.InvalidKindError

And again, after running ``make html``, the output will be the same as before.

Generating comprehensive API references
---------------------------------------

While using ``sphinx.ext.autodoc`` makes keeping the code 
and the documentation in sync much easier, 
it still requires you to write an ``auto*`` directive for every object you want to document. 
Sphinx provides yet another level of automation: the autosummary extension.

The ``autosummary`` directive generates documents 
that contain all the necessary autodoc directives. 
To use it, first enable the autosummary extension:

``docs/source/conf.py``

::

 extensions = [
    'sphinx.ext.duration',
    'sphinx.ext.doctest',
    'sphinx.ext.autodoc',
    'sphinx.ext.autosummary',
 ]

Next, create a new api.rst file with these contents:

``docs/source/api.rst``

::

 API
 ===
 
 .. autosummary::
    :toctree: generated
 
    lumache

Remember to include the new document in the root toctree:

``docs/source/index.rst``

::

 Contents
 --------
 
 .. toctree::
 
    usage
    api

Finally, after you build the HTML documentation running make html, it will contain two new pages:

- ``api.html``, corresponding to ``docs/source/api.rst`` and containing a table with the objects you included in the autosummary directive (in this case, only one).

- ``generated/lumache.html``, corresponding to a newly created reST file ``generated/lumache.rst`` and containing a summary of members of the module, in this case one function and one exception.

.. figure:: ../images/016-lumache-autosummary.png
   :align: center
   
   Summary page created by autosummary

Each of the links in the summary page will take you to the places 
where you originally used the corresponding autodoc directive, 
in this case in the ``usage.rst`` document.

.. note::

    The generated files are based on Jinja2 templates that can be customized, 
    but that is out of scope for this tutorial.