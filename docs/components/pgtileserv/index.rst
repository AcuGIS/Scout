.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
pg_tileserv
**********************

.. contents:: Table of Contents

pg_tileserv
==================

pg_tileserv is installed as a systemd service during installation.

The service can be started and stopped via command line or Webmin.

The service file contents are show below.

.. code-block:: console
   :linenos:

	[Unit]
	Description=PG TileServ
	After=multi-user.target

	[Service]
	User=pgis
	WorkingDirectory=/opt/pg_tileserv
	Type=simple
	Restart=always
	ExecStart=/opt/pg_tileserv/pg_tileserv --config /opt/pg_tileserv/config/pg_tileserv.toml
	
	[Install]
	WantedBy=multi-user.target

The file is installed at::

	/etc/systemd/system/pg_tileserv.service


Command Line
============

Service commands:

.. code-block:: console
   :linenos:

   root@postgis:~# service pg_tileser stop | start 
   
Access
============

pg_tileserv runs of port 7800 and can be accessed at http://doamin.com:7800

You can change the port via the pg_tileserv.toml file located under /opt/pg_tileserv/config
   
Webmin
============

To start and stop the pg_tileserv service, click the button as below.

.. image:: _static/pgtileserv.png


Database
=========

On installation, a database is created called postgisftw.  

This database contains the demo data.

A user pgis is also created and given permission to the database.  

The password for pgis is displayed at the end of installation as well as saved to /root/auth.txt

 
Structure
==========

pg_tileserv is installed by default at::

	/opt/pgtileserv

The directory structure is show below::
	
	/opt/pg_tileserv
	├── LICENSE.md
	├── README.md
	├── assets
	    ├── index.html
	    ├── preview-function.html
	    └── preview-table.html
	├── config
	    ├── pg_tileserv.toml
	    └── pg_tileserv.toml.example.save
	└── pg_tileserv


Configuration File
==================

On installation, the pg_tileserv.toml configuration file is updated to include the postgisftw connection inforation::

	DbConnection = "postgresql://pgis:G84iwLdL9jeyA7IiwkTmWhyHwKR41Qxz@localhost/postgisftw"
	

https://github.com/CrunchyData/pg_tileserv

 


