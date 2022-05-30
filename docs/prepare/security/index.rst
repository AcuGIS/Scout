	
  .. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Security
**********************

Always create your table using a minimally privlaged user.

Below, we'll create a new user, 'minuser' with only the required permissions for the table 'mytable'.

.. code-block:: console

  CREATE ROLE minuser LOGIN PASSWORD 'password';

Grant Connect on the database

.. code-block:: console

  GRANT CONNECT ON DATABASE mydb TO minuser;
  
Grant SELECT, INSERT, and UPDATE on table 'mytable'

.. code-block:: console

 GRANT SELECT, INSERT, UPDATE ON mytable TO minuser;
