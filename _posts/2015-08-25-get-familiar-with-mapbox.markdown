---
layout: post
title: Get Familiar With Mapbox
date: 2015-08-25 19:09:11.000000000 +05:30
---

# Prerequisites
-> Should have account with Mapbox inorder to use 
-> Should be familiar with leaflet library

# Advantages
-> Ease of use
-> Customize styling, colourize
-> Vector maps
-> Static maps 
-> Retina Tiles default comes with mapbox
-> Open Source
and much more

When we explore any maps, we can see different locations that include within the single continuous image. That single image what we called map consists of zoom in and out to explore different areas and we called this single image as Map.

This map or this large image holds large amount of data with, in reality these maps are made of small tiny square images called <b>tiles</b>.

Mapbox javascript api will take cares of downloading these tiles based on zoom level, and coordinates(x,y positions).

A map is made of layers, lets suppose say that we've seen some markers in any map that means we had one layer on top of map. Layers can be images, lines, markers. Leaflet uses inheritance and nesting.

### Tile Layer
<code>
  L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png?{foo}', {foo: 'bar'}).addTo(map);
  # https://www.mapbox.com/mapbox.js/api/v2.2.0/l-tilelayer/
  # We can also pass map.id on tileLayer.
</code>


### Layer Groups
As the name suggest we can create layer groups 
<code>
  var layerGroup = L.layerGroup().addTo(map);
  L.mapbox.tileLayer('map.id1').addTo(layerGroup);
  L.mapbox.tileLayer('map.id2').addTo(layerGroup);
</code>
  
### GeoJSON and Feature Layer
  GeoJson is a format used to structure data that's required to build a map. This is the common way to transfer geodata.
  
<code>
  # http://geojson.org/
</code>
 
  GeoJSON extends featureLayer which has a little flexibility of handling data by
   -> Load GeoJSON via Ajax
   -> Filter using setFilter
   -> Style with [simple-style-spec](https://www.mapbox.com/guides/an-open-platform/#simplestyle)

### Add Marker

<code>
L.marker(<LatLng> latlng,<Marker options> options? )
</code>

Instantiates a Marker object given a geographical point and optionally an options object. We can add marker latlong and some optional options. 

Check geojson.org for reference.


### To load Multiple markers 

<code>
  L.mapbox.featureLayer(id|url|geojson, options)
  // geojson format should follow geojson.org
</code>

### Icons in markers

<code>
var myIcon = L.icon({
	iconUrl: 'my-icon.png',
	iconSize: [38, 95],
    className: 'icon'
});

L.marker(geocodes, {title: '', icon: myIcon}
</code>

### Multiple markers
Use Geojson
Represents a GeoJSON layer. Allows you to parse GeoJSON data and display it on the map. Extends FeatureGroup.

### Event handlers 
 Event   - Method
 attach  - on 
 detach  - off 
 trigger - fire
 Events list for referenced object - hasEventListeneres
 Remove Events - removeEventListeners - 
  
**Example**
<code>
  marker.on('click', function(event){})
  
  where event = {type: 'click', target: [object]}
  
  Documentation at leaflet library
   -> eventmethods
   -> eventobjects
</code>
 
### Static maps
 
 Static maps are maps that doesnt require all functionalities of map and to show some particular map. Best example at contact us section.
  
 Documentation at mapbox webservices , static maps
  
 Icons for mapbox static maps available at mapbox maki https://mapbox.com/maki
  
### Vector maps 
 
  Include mapbox webgl css and js
  
  where webgl is a standard support that should include in browsers 
  
  Instead of L prefix we'll use
  
   mapboxgl.accessToken = "..."
   
### Geocoding API
Converts Lat, long into location text and vice versa.

Forward Geocoding: 
<code>
# https://api.mapbox.com/v4/geocode/{dataset}/{query}.json?access_token=<your access token>
</code>

- Index (dataset for querying means like database to query from. Cities, countries or from global )
- query (string query replacing spaces with + signs )
- Token ( api access token)
- https://www.mapbox.com/developers/api/geocoding/
- 
Guides :: 
mapbox.com/foundations
Mapbox studio:: tool for creating style maps
mapbox.com/mapbox-studio
leaflet plugins:: leafletjs.com/plugins.html