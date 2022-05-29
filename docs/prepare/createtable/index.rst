	
  .. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Create Table
**********************

The minimum requirements are four columns 'id', 'location', 'latlngalt',  and 'timestamp'

Create the table in PostgreSQL:

.. code-block:: console

	CREATE TABLE mytable (
    	id integer DEFAULT nextval('public.my_id_seq'::regclass) NOT NULL,
    	location point,
    	latlngalt json,
    	"timestamp" timestamp without time zone
	);

AcuGIS Scout is programmed to ignore Primary auto-incremented key when creating forms.

So create an appropriate sequence

.. code-block:: console

	CREATE SEQUENCE public.my_id_seq
    	START WITH 1
    	INCREMENT BY 1
    	NO MINVALUE
    	NO MAXVALUE
    	CACHE 1;
	
In the next section, we'll look at optional field data types.
