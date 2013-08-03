.. _hacks:

================
Hacking jsFiddle
================

.. note::

 Working with CoffeeScript no longer requires you to hack jsFiddle.
 Please visit :ref:`panels`.

Sometimes jsFiddle does not provide the feature you'd expect. Below is a small
collection of working, non-harmful hacks.


.. _css_panel_hack:

CSS panel ``</style>`` hack
###########################
If you need to edit the ``<head>`` of a page, you can do that by
closing the ``style`` element that your CSS is placed into.
After all additions to the ``head``, you should open the ``style`` tag again.

.. code-block:: css
  
 /* your custom CSS */
 </style>
 <!-- access to the HEAD element -->
 <style>

Inserting the above code into the CSS panel will change the CSS section of the ``head`` to

.. code-block:: html

 <style type='text/css'>
 /* your custom CSS */
 </style>
 <!-- access to the HEAD element -->
 <style>
 </style>


.. _paperscript_hack:

Working with PaperScript
########################
In short: fork http://jsfiddle.net/zalun/xvhFa/ to start a PaperScript_ fiddle.

.. _PaperScript: http://paperjs.org/tutorials/getting-started/working-with-paper-js/

Similar to CoffeeScript, Paperscript requires the ``script`` tag to have a
``type`` of ``text/paperscript`` and provide the ``id`` of the ``canvas``
element in the ``canvas`` parameter. Enter the following into the HTML panel and
you'll be able to write Paperscript in the JavaScript panel.

.. code-block:: html

 <canvas id="some-unique-id" resize keepalive="true" style='height: 200; width: 200;'></canvas>
 <script>(function(){var s="script",n='\n',d=document,b=d.getElementsByTagName(s)[2].innerHTML.split(n);d.write('<'+s+' type="text/paperscript" canvas="' + document.getElementsByTagName('canvas')[0].id + '">'+b.slice(2,b.length-2).join(n)+'</'+s+'>')})()</script>

Please set the **Code Wrap** to ``no wrap - in <head>`` (the default is ``onLoad``) and
**Framework** to ``No-library (pure JS)``.

As PaperScript requires this hack to work, we can't add it to the list of
frameworks yet. Add a link to 
https://raw.github.com/paperjs/paper.js/master/dist/paper.js
as a **Resource** (:ref:`add_resources`).

Example PaperScript jsFiddle: http://jsfiddle.net/zalun/LrGEm/12/
