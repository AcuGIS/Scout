.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
pg_featureserv
**********************

.. contents:: Table of Contents

pg_featureserv
==================

pg_featureserv is installed as a systemd service during installation.

The service can be started and stopped via command line or Webmin.

The service file contents are show below.

.. code-block:: console
   :linenos:

	[Unit]
	Description=PG FeatureServ
	After=multi-user.target

	[Service]
	User=pgis
	WorkingDirectory=/opt/pg_featureserv
	Type=simple
	Restart=always
	ExecStart=/opt/pg_featureserv/pg_featureserv --config /opt/pg_featureserv/config/pg_featureserv.toml

	[Install]
	WantedBy=multi-user.target


The file is installed at::

	/etc/systemd/system/pg_featureserv.service


Command Line
============

Service commands:

.. code-block:: console
   :linenos:

   root@postgis:~# service pg_featureserv stop | start 
   
Access
============

pg_tileserv runs of port 9000 and can be accessed at http://doamin.com:9000

You can change the port via the pg_featurserv.toml file located under /opt/pg_featurserv/config
   
   
Webmin
============

To start and stop the pg_tileserv service, click the button as below.

.. image:: _static/pgfeaturserv.png


Database
=========

On installation, a database is created called postgisftw.  

This database contains the demo data.

A user pgis is also created and given permission to the database.  

The password for pgis is displayed at the end of installation as well as saved to /root/auth.txt

 
Structure
==========

pg_tileserv is installed by default at::

	/opt/pgfeatureserv

The directory structure is show below::
	
	/opt/pg_featureserv
	├── LICENSE.md
	├── README.md
	├── assets
	│   ├── api.gohtml
	│   ├── collection.gohtml
	│   ├── collections.gohtml
	│   ├── conformance.gohtml
	│   ├── fun_script.gohtml
	│   ├── function.gohtml
	│   ├── functions.gohtml
	│   ├── home.gohtml
	│   ├── item.gohtml
	│   ├── items.gohtml
	│   ├── map_script.gohtml
	│   └── page.gohtml
	├── config
	│   ├── pg_featureserv.toml
	│   └── pg_featureserv.toml.example.save
	└── pg_featureserv



Configuration File
==================

On installation, the pg_featureserv.toml configuration file is updated to include the postgisftw connection inforation::

	DbConnection = "postgresql://pgis:G84iwLdL9jeyA7IiwkTmWhyHwKR41Qxz@localhost/postgisftw"
	

https://github.com/CrunchyData/pg_featureserv
 


