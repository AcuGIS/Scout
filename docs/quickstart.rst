**********************
Quic Start
**********************

Below is the Quick Start

1. Create a table in PostgreSQL using below:

.. code-block:: console

	CREATE SEQUENCE public.my_id_seq
    	START WITH 1
    	INCREMENT BY 1
    	NO MINVALUE
    	NO MAXVALUE
    	CACHE 1;

	CREATE TABLE mytable (
    	id integer DEFAULT nextval('public.my_id_seq'::regclass) NOT NULL,
      	title character varying(200),
      	qr character varying(200),
    	location point,
    	latlngalt json,
    	"timestamp" timestamp without time zone
	);

2. Install Scout on your iOS or Android Device

3. Add your PostgreSQL connection details.

 .. image:: _static/add-connection-small.jpg  

4. Start adding data

 .. image:: _static/scout-menu-small.jpg  


