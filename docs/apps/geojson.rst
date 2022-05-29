.. _jri-label:
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Leaflet GeoJson
**********************

.. contents:: Table of Contents


Access
=================

A web application employing LeafletJS and GeoJson is enabled upon installation.

It can be access via the Leaflet tab on the home page:

.. image:: _static/leaflet-tab.png

It can also be access directly via url at::

   http://domain.com/LeafletJSDemo.html
   
   

Usage
=================

Once accessed using above, the app will appear as shown below:

.. image:: _static/leaflet-app1.png

Click on the US layer to view the getFeature info for the State.

The data will be displayed as below:

.. image:: _static/leaflet-app.png
   

Structure
=============

The app is located at::

	/vaw/www/html/LeafletJSDemo.html
		
On installation, data from PostgreSQL is exported to GeoJson format and saved to::

	/var/www/html/states.json
	

Content
=========

The content of the html page is displayed below.

.. code-block:: console
   :linenos:

	<!doctype html>
	<html>
	<head>
  	<style type="text/css">
    	body {
      	padding: 0;
      	margin: 0;
    	}

    	html, body, #map {
      	height: 100%;
    	}

  	</style>

	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.1.0/dist/leaflet.css"
   	integrity="sha512-wcw6ts8Anuw10Mzh9Ytw4pylW8+NAD4ch3lqm9lzAsTxg0GFeJgoAtxuCLREZSC5lUXdVyo/7yfsqFjQ4S+aKw=="
   	crossorigin=""/>

    	<script src="https://unpkg.com/leaflet@1.1.0/dist/leaflet.js"
   	integrity="sha512-mNqn2Wg7tSToJhvHcqfzLMU6J4mkOImSPTxVZAdo+lcPlk+GhZmYgACEe0x35K7YzW1zJ7XyJV/TT1MrdXvMcA=="
   	crossorigin=""></script>
  	</head> 
  
	<script src="http://code.jquery.com/jquery-2.1.0.min.js"></script>
	</head>
	<body>
  	<div id="map"></div>
  	<script>
	var osmUrl='http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png';
  	var osmAttrib='Data &copy <a href="http://openstreetmap.org">OpenStreetMap</a> contributors';
  	var osm = new L.TileLayer(osmUrl, {minZoom: 2, maxZoom: 8, attribution: osmAttrib});
    
    	$.getJSON("states.geojson", function(data) {
	function onEachFeature(feature, layer) {
        layer.bindPopup("Name: " + feature.properties.STATE_NAME + "<br>" + "Abbreviation: " + feature.properties.STATE_ABBR);
  	}   
	var geojson = L.geoJson(data, {
      	onEachFeature: onEachFeature
    	});
	
    	var map = L.map('map').fitBounds(geojson.getBounds());
    	osm.addTo(map);
    	geojson.addTo(map);
  	});
	  </script>
	</body>
	</html>


Documentation
==============
https://leafletjs.com/

https://leafletjs.com/examples/geojson/
   
