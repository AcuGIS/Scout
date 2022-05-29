	
  .. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Images
**********************

Image columns must be of the Data Type bytea

The column name can be anything you wish.  Below, we are using 'myimage'

You can add as many image columns as wish as well

Create the table in PostgreSQL with image field:

.. code-block:: console

	CREATE TABLE mytable (
    	id integer DEFAULT nextval('public.my_id_seq'::regclass) NOT NULL,
	myimage bytea,
    	location point,
    	latlngalt json,
    	"timestamp" timestamp without time zone
	);

Images are stored in the column as bytea binary files.
