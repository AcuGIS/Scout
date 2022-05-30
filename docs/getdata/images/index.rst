.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Images
**********************

Images can be queried directly from the database, of course, for rendering into your applications.

If you wish to pull images directly from the database to the file system, you can use similar to below

.. code-block:: console

   psql -d mydb -Aqt -c "SELECT encode(myimagecol, 'base64') FROM mytable where id=88" | base64 -d > mypicture.png

