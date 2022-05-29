	
  .. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Altitude
**********************

The altitude column, 'latlngalt' is mandatory and stores altitude as well as lat/lon as json type.

Create the table in PostgreSQL:

.. code-block:: console

	CREATE TABLE mytable (
    	id integer DEFAULT nextval('public.my_id_seq'::regclass) NOT NULL,
    	location point,
    	##latlngalt json,##
    	"timestamp" timestamp without time zone
	);


