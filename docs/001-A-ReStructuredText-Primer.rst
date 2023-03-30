A ReStructuredText Primer
=========================

源教程地址: https://docutils.sourceforge.io/docs/user/rst/quickstart.html .

这是一个 **ReStructuredText** 快速教程，更详细的教程位 `Quick reStructuredText <https://docutils.sourceforge.io/docs/user/rst/quickref.html>`_ 。

Structure
---------

`paragraph <https://docutils.sourceforge.io/docs/user/rst/quickref.html#paragraphs>`_ 是最简单的结构，不同的段落用一个 **空行** 分隔，段落必须有相同的缩进，如： ::

   This is a paragraph.  It's quite
   short.

      This paragraph will result in an indented block of
      text, typically used for quoting other text.

   This is another one.

结果：

This is a paragraph.  It's quite
short.

   This paragraph will result in an indented block of
   text, typically used for quoting other text.

This is another one.

Text styles
-----------

`内联标记 <https://docutils.sourceforge.io/docs/user/rst/quickref.html#inline-markup>`_ 包括斜体和粗体。

*斜体* 、 **粗体** 和 ``固定空间字体`` ： ::

   *斜体* 、 **粗体** 和 ``固定空间字体``






.. _installation:

Installation
------------

To use Lumache, first install it using pip:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

