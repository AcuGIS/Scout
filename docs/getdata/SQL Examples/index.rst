.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
JSON SQL Examples
**********************

While lat/lon is stored in the location column as a Point, altitude is stored in a json array (along with lat/lon) in the latlngalt column.

A standard select query such as 'select latlngalt from mytable', latwould produce as below:


"{""latitude"":""41.7408504"",""longitude"":""87.9883978"",""altitude"":""327.3999938964844""}"
"{""latitude"":""27.657320220545436"",""longitude"":""-81.2845245094787"",""altitude"":""22.593265533447266""}"


To query altitude value alone, use the json operators >> for text:

.. code-block:: console

select latlngalt->>'altitude' from mytable;

Which produces the values for altitude as text.

To select the values as json, use the 'short' arrow

.. code-block:: console

select latlngalt->>'altitude' from mytable;
