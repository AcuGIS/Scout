**********************
Convert to Geometry
**********************

lat/lon is stored in the location column as a Point.

This is done to make the app useful to PostgreSQL users who do not have (or want) PostGIS enabled.

A select of the location column will produce an output like below::

  (28.657320220545436,-81.2845245094787)
  (31.7408504,34.9883978)

To convert the location column to Geometry type Point, you can use below

.. code-block:: console

   select ST_SetSRID((location)::GEOMETRY(POINT), 4326) from mytable;

This will provide an output similar to below::

  0101000020E6100000FE3D522346A83C40C6C749A6355254C0
  0101000020E6100000803A2F5FA8BD3F401C38B1D1837E4140

To convert to this output WKT, we can use st_asewkt as below:

.. code-block:: console

   SELECT st_asewkt(ST_SetSRID((location)::GEOMETRY(POINT), 4326)) from mytable;
   
This will provide the output in WKT format as below::

  SRID=4326;POINT(28.657320220545436 -81.2845245094787)
  SRID=4326;POINT(31.7408504 34.9883978)
  
If you wish to automate this, you can create a trigger like below to update a geom column within the table or in another table

.. code-block:: console

  CREATE OR REPLACE FUNCTION togeom() RETURNS trigger
     LANGUAGE plpgsql AS
  $$BEGIN 
     NEW.geom = (select ST_SetSRID((new.location)::GEOMETRY(POINT), 4326) from qt LIMIT 1);
    RETURN NEW; 
  END;$$;

  CREATE OR REPLACE TRIGGER update_geom 
     AFTER INSERT ON qt FOR EACH ROW
    EXECUTE PROCEDURE togeom();
