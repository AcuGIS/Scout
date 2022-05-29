	
  .. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Apache
**********************

.. contents:: Table of Contents


About
=================

For purposes of caching, Apache is configured to run on an irregular port for both HTTP and HTTPS.

This port is then used to accept requests via Varnish and Hitch.


Usage
=================

Apache can be stopped and started via Servers > Apache HTTP Server

You can also stop/start/restart Apache via command line.

For Ubuntu::

  service apache2 stop | stop | restart | status
  
For CentOS::

  service httpd stop | stop | restart | status
   

Configuration
=============

The main Apache configuration file, 000-default.conf is located at::

	/etc/apache2/sites-enabled/000-default.conf
  
For CentOS, it is located at::

  /etc/httpd/000-default.conf
		

As shown below, we configure a location 'tile' and 'feature' to proxy requests to pg_tileserv and pg_featureserv::

	  ProxyPass 	 /tile http://localhost:7800/tile
	  ProxyPassReverse /tile http://localhost:7800/tile

	  ProxyPass 	 /feature http://localhost:9000/feature
	  ProxyPassReverse /feature http://localhost:9000/feature
    
An alternative approach is to assign a sub domain to each endpoint.

For example, tile.domain.com and feature.domain.com, and then map directly to their ports.
		
Documentation
==============
https://httpd.apache.org/ 


