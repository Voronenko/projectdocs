====================
Codeblock's examples
====================

Using highlight directive
-------------------------

.. highlight:: html

The literal blocks are now highlighted as HTML, until a new directive is found.

::
   <html><head></head>
   <body>This is a text.</body>
   </html>

The following directive changes the hightlight language to SQL.

.. highlight:: sql

::
   SELECT * FROM mytable

.. highlight:: none

From here on no highlighting will be done.

::
   SELECT * FROM mytable


Using code-block
----------------


sql - Structured Query Language
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following is a SQL statement.

.. code-block:: sql
   :linenos:

   SELECT * FROM mytable

PostgreSQL - PostgreSQL dialect of SQL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following is a PostgreSQL statement.

.. code-block:: postgresql
  :linenos:

  SELECT name FROM employee WHERE id IN (SELECT id FROM job WHERE title ~ '^[A-E]');


RST - ReStructured Text
~~~~~~~~~~~~~~~~~~~~~~~


.. code-block:: rst

  .. code-block:: postgresql
    :linenos:

    SELECT name FROM employee WHERE id IN (SELECT id FROM job WHERE title ~ '^[A-E]');


bat - DOS/Windows batch file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~


.. code-block:: bat
  :linenos:

  @ECHO OFF
  :: Check for NT4 or later
  IF NOT "%OS%"=="Windows_NT" GOTO Syntax
  :: Check for XP or later
  FOR /F "tokens=2 delims=[]" %%A IN ('VER') DO FOR /F "tokens=2" %%B IN ("%%~A") DO IF %%B LSS 5.1 GOTO Syntax

  :: Check command line argument
  IF     "%~1"=="" GOTO Syntax
  IF NOT "%~2"=="" IF /I NOT "%~2"=="/A" GOTO Syntax
  ECHO.%1 | FINDSTR /R /C:"[:\\\*\?,;/]" >NUL && GOTO Syntax

  :: If the specified command contains a dot, it is not a macro nor an internal command
  ECHO.%1 | FIND "." >NUL && GOTO ExtCmd


powershell - Windows PowerShell
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


.. code-block:: powershell
  :linenos:

  # PowerShell example to find Windows log files
  Clear-Host
  $Directory = "C:\Windows\"
  $Files = Get-Childitem $Directory -recurse -Include *.log `
  -ErrorAction SilentlyContinue


bash - Bash shell scripts
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash
  :linenos:


  #!/bin/bash

  set -e

  make


######################################

Standard reST literal blocks are started by ``::``
at the end of the preceding paragraph and delimited by indentation.

Highlight directive
*******************

The default highlighting language is Python:
it can be be changed using the ``highlight`` directive
within a document::

   .. highlight:: html

   The literal blocks are now highlighted as HTML, until a new directive is found.

   ::
      <html><head></head>
      <body>This is a text.</body>
      </html>

   The following directive changes the hightlight language to SQL.

   .. highlight:: sql

   ::
      SELECT * FROM mytable

   .. highlight:: none

   From here on no highlighting will be done.

   ::
      SELECT * FROM mytable


Code-block directive
********************

The ``code-block`` directive can be used to declare the specific language
to be used in a block, regardless of the highlighting language::

   The following is a SQL statement.

   .. code-block:: sql
      :linenos:

      SELECT * FROM mytable

Line numbers are useful for long blocks such as this one:

.. code-block:: postgresql
   :linenos:

   -- http://www.postgresonline.com/journal/index.php?/archives/97-SQL-Coding-Standards-To-Each-His-Own-Part-II.html
   SELECT persons.id, persons.first_name, persons.last_name, forums.category,
      COUNT(DISTINCT posts.id) as num_posts,
      COALESCE(MAX(comments.rating), 0) AS highest_rating,
      COALESCE(MIN(comments.rating), 0) AS lowest_rating
   FROM persons JOIN posts ON persons.id = posts.author
      JOIN forums on posts.forum = forums.id
      LEFT OUTER JOIN comments ON posts.id = comments.post
   WHERE persons.status > 0
      AND forums.ratings = TRUE
      AND comments.post_date > ( now() - INTERVAL '1 year')
   GROUP BY persons.id, persons.first_name, persons.last_name, forums.category
   HAVING count(DISTINCT posts.id) > 0
   ORDER BY persons.last_name, persons.first_name;

Literalinclude directive
************************

Another option is to include part of a given source code file, like this::

      .. literalinclude:: filename
         :linenos:
         :language:
         :lines:
         :start-after:
         :end-before:
         :emphasize-lines:

Just below is a example:

.. literalinclude:: rst_codeblocks.rst
   :language: rst
   :lines: 93-96

Instead of using line numbers (which can change), it is possible to
use the options ``:start-after`` and ``:end-before:``
that search the included file for lines containing the specified text.
For example::

   .. literalinclude:: rst_codeblocks.rst
      :language: rst
      :start-after: Instead of using
      :end-before: For example

produces this result:

.. literalinclude:: rst_codeblocks.rst
      :language: rst
      :start-after: Instead of using
      :end-before: For example


Pygments lexers
***************

Syntax highlighting is done by Pygments (if installed):
any of the `Pygments language lexers` can be used.

The following table lists some useful lexers (in no particular order).

.. _pygments-lexers-ref:

.. list-table::
   :header-rows: 1

   *  -  Lexer
      -  Shortname

   *  -  Structured Query Language
      -  sql

   *  -  PostgreSQL dialect of SQL
      -  postgresql

   *  -  PostgreSQL procedural language
      -  plpgsql

   *  -  PostgreSQL console sessions
      -  psql

   *  -  ReStructured Text
      -  rst

   *  -  TeX and LaTeX
      -  latex

   *  -  DOS/Windows batch file
      -  bat

   *  -  Windows PowerShell
      -  powershell

   *  -  Bash shell scripts
      -  bash

   *  -  Bash shell sessions
      -  console

   *  -  Cascading Style Sheets
      -  css

   *  -  HTML 4 and XHTML 1
      -  html

   *  -  XML
      -  xml

   *  -  XSLT
      -  xslt

   *  -  XQuery
      -  xquery

   *  -  JavaScript
      -  javascript

   *  -  JSON data structures
      -  json

   *  -  PHP source code
      -  php

   *  -  PHP embedded in HTML
      -  html+php

   *  -  Python 2
      -  python

   *  -  Python 2 tracebacks
      -  pytb

   *  -  Python console
      -  pycon

   *  -  Java
      -  java

   *  -  Configuration file in the Java's properties format
      -  jproperties

   *  -  Configuration file in the Apache config file format
      -  apacheconf

   *  -  R source code (or S, or S-plus)
      -  r

   *  -  R console
      -  rout

   *  -  Matlab
      -  matlab

   *  -  Matlab sessions
      -  matlabsession

   *  -  NumPy
      -  numpy
