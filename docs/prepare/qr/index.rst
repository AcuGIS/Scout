	
  .. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
QR Scanner
**********************

All varchar columns will have the option to use QR Scan

The column name can be anything you wish.  Below, we are using 'myqr'

You can add as many varchar columns as wish as well

Create the table in PostgreSQL with image field:

.. code-block:: console

	CREATE TABLE mytable (
    	id integer DEFAULT nextval('public.my_id_seq'::regclass) NOT NULL,
    	myqr character varying(200),
    	location point,
    	latlngalt json,
    	"timestamp" timestamp without time zone
	);

QR values are stored as text in the database
