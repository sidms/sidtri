---
layout: post
title: Google Maps
---
To build a map we need map options and map node

<pre>
 <code class='language-javascript'>
 		# Javascript
 		var options = {
 			center: {
 				lat: '',
 				lng: ''
 			},
 			zoom: 10
 		}

 		element = document.getElementById('map-canvas')
 		map = new google.maps.Map(element, options);

 		# Css
 		#map-canvas{
 			width: 100%;
 		}

 </code>
</pre>

#html
<body>
	<div id='map-canvas'> 
	</div>
</body>


And you are done..





other options :: 
disableDefaultUI: true  # hides zooming
scrollwheel: true
draggable: false # map fixed
mapTypeId: google.maps.mapTypeId.Satellite, Roadmap
maxZoom: 11
minZoom: 9
zoomControlOptions: {
	position: google.maps.ControlPosition.bottom_left
}


