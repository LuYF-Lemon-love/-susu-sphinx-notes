001 A ReStructuredText Primer
=============================

源教程地址: https://docutils.sourceforge.io/docs/user/rst/quickstart.html 。

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

可以使用 ``\`` 进行 `转义 <https://docutils.sourceforge.io/docs/user/rst/quickref.html#escaping>`_ 。

注意: 内联标记前后要有空格。

Lists
-----

列表有三种主要形式：枚举、项目符号和定义，列表元素左侧要对齐。

列表前一行必须是一个空行。

`枚举列表 <https://docutils.sourceforge.io/docs/user/rst/quickref.html#enumerated-lists>`_

以数字或字母开头，后跟句点 ``.`` ， 右括号 ``)`` 或被括号 ``( )`` 包围： ::

   1. numbers

   A. upper-case letters
      and it goes over many lines

      with two paragraphs and all!

   a. lower-case letters

      3. with a sub-list starting at a different number
      4. make sure the numbers are in the correct sequence though!

   I. upper-case roman numerals

   i. lower-case roman numerals

   (1) numbers again

   1) and again

结果（列表样式不是每个 Web 浏览器始终支持）：

1. numbers

A. upper-case letters
   and it goes over many lines

   with two paragraphs and all!

a. lower-case letters

   3. with a sub-list starting at a different number
   4. make sure the numbers are in the correct sequence though!

I. upper-case roman numerals

i. lower-case roman numerals

(1) numbers again

1) and again

`项目符号列表 <https://docutils.sourceforge.io/docs/user/rst/quickref.html#bullet-lists>`_

以一个项目符号（ ``-`` 、 ``+`` 、 ``*`` ）开始： ::

   * a bullet point using "*"

     - a sub-list using "-"

       + yet another sub-list

     - another item

结果:

* a bullet point using "*"

  - a sub-list using "-"

    + yet another sub-list

  - another item

`定义列表 <https://docutils.sourceforge.io/docs/user/rst/quickref.html#definition-lists>`_

与其他两个不同，定义列表由一个术语组成，和该术语的定义。定义列表的格式为： ::

 what
   Definition lists associate a term with a definition.

 *how*
   The term is a one-line phrase, and the definition is one or more
   paragraphs or body elements, indented relative to the term.
   Blank lines are not allowed between term and definition.

结果:

what
  Definition lists associate a term with a definition.

*how*
  The term is a one-line phrase, and the definition is one or more
  paragraphs or body elements, indented relative to the term.
  Blank lines are not allowed between term and definition.

Codes
------

`Codes <https://docutils.sourceforge.io/docs/user/rst/quickref.html#literal-blocks>`_

代码的前一行以 ``::`` 结尾，代码片段要进行缩进。 ::

 An example::

     Whitespace, newlines, blank lines, and all kinds of markup
       (like *this* or \this) is preserved by literal blocks.
   Lookie here, I've dropped an indentation level
   (but not far enough)

 no more example

结果:

An example::

    Whitespace, newlines, blank lines, and all kinds of markup
      (like *this* or \this) is preserved by literal blocks.
  Lookie here, I've dropped an indentation level
  (but not far enough)

no more example

如果 ``::`` 自成一段，将被删除： ::

 ::

     This is preformatted text, and the
     last "::" paragraph is removed

结果：

::

    This is preformatted text, and the
    last "::" paragraph is removed

Sections
--------

`section headers <https://docutils.sourceforge.io/docs/user/rst/quickref.html#section-structure>`_ 是一个被如下符号装饰的单行文本: ``下划线`` 、``下划线和上划线`` 、破折号 ``-----`` 、等号 ``======`` 、波浪号 ``~~~~~~`` 、或任何非字母数字字符 ``= - ` : ' " ~ ^ _ * + # < >`` 。其中下划线/上划线必须至少与标题文本一样长。所有标有相同装饰风格的 sections 都被视为处于同一级别： ::

 Chapter 1 Title
 ===============

 Section 1.1 Title
 -----------------

 Subsection 1.1.1 Title
 ~~~~~~~~~~~~~~~~~~~~~~

 Section 1.2 Title
 -----------------

 Chapter 2 Title
 ===============

结果（通过简化的伪XML进行说明）：

::

 <section>
     <title>
         Chapter 1 Title
     <section>
         <title>
             Section 1.1 Title
         <section>
             <title>
                 Subsection 1.1.1 Title
     <section>
         <title>
             Section 1.2 Title
 <section>
     <title>
         Chapter 2 Title

节标题可用作链接目标，仅仅使用它们的名字。为了链接 Lists_ 可以使用 ``Lists_`` ，为了链接有空格的 `text styles`_ 可以使用 ```text styles`_`` 。

Document Title / Subtitle
-------------------------

整个文档的标题与章节标题不同，格式可能略有不同（默认情况下，HTML 编写器将其显示为居中标题）。

要在 reStructuredText 中指示文档标题，请在文档开头使用独特的修饰样式。要指示文档副标题，请在文档标题之后立即使用另一种独特的装饰样式。例如：

::

 ================
  Document Title
 ================
 ----------
  Subtitle
 ----------
 
 Section Title
 =============
 
 ...

Images
-------

`Images <https://docutils.sourceforge.io/docs/user/rst/quickref.html#directives>`_

::

 .. image:: ../images/001-susu.jpeg

结果：

.. image:: ../images/001-susu.jpeg

如果图像要以 HTML 形式出现，并且您希望提供其他信息，您可以：

::

 .. image:: ../images/001-susu.jpeg
    :height: 100
    :width: 200
    :scale: 50
    :alt: alternate text

结果：

.. image:: ../images/001-susu.jpeg
   :height: 100
   :width: 200
   :scale: 50
   :alt: alternate text

更多的信息可以参考 https://docutils.sourceforge.io/docs/ref/rst/directives.html#images 。

What Next?
----------

1. https://docutils.sourceforge.io/docs/user/rst/quickref.html 。

2. https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html 。
