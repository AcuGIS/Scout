.. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Hitch
**********************

.. contents:: Table of Contents


About
=================

Hitch is an SSL/TLS proxy.

It accepts request in HTTPS and converts them to HTTP for Varnish.
   

Usage
=================

Hitch can be stoped, started, and restarted via command line::

  service hitch stop | stop | restart | status
   

Configuration
=============

The main hitch configuration file, hitch.conf is located at::

	/etc/hitch/hitch.conf
		
The content will appear similar to below::
  
  tls-protos = TLSv1.2 TLSv1.3

          frontend = {
          host = "*"
          port = "443"
          }

          backend = "[127.0.0.1]:8443"
          workers = 2
          write-proxy-v2 = on
          daemon = off
          user = "_hitch"
          group = "_hitch"
          pem-file= "/etc/letsencrypt/live/domain.com/bundle.pem"
          alpn-protos = "h2, http/1.1" 
          log-level = 1
          
          
Note that Hitch accepts requests on the HTTPS 443 port and sends them via port 8443 to Varnish.

.. Note:: 
   If you change the SSL file location, it will need to be updated in above. 


Documentation
==============
https://hitch-tls.org/   
