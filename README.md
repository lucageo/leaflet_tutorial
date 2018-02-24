# leaflet_tutorial
Leaflet Tutorial

```
<html>
<head>
  <title>A Leaflet map!</title>
  <link rel="stylesheet" href="leaflet.css"/>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet.markercluster/1.3.0/MarkerCluster.Default.css"/>
  <script src="leaflet.js"></script>
   <script src="jquery.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet.markercluster/1.3.0/leaflet.markercluster-src.js"></script>

  <style>
    #map{ height: 100% }
  </style>
</head>
<body>

  <div id="map"></div>

  <script>

  // initialize the map

  var map = L.map('map').setView([42.35, -71.08], 13);

  // load a tile layer
  L.tileLayer('http://tiles.mapc.org/basemap/{z}/{x}/{y}.png',
    {
      attribution: 'Tiles by <a href="http://mapc.org">MAPC</a>, Data by <a href="http://mass.gov/mgis">MassGIS</a>',
      maxZoom: 17,
      minZoom: 9
    }).addTo(map);

  // load GeoJSON from an external file




  </script>
</body>
</html>

```
##### Add the following to call (ajax) the json file and create points
```
  $.getJSON("https://maptimeboston.github.io/leaflet-intro/rodents.geojson",function(data){

    L.geoJson(data,{
      pointToLayer: function(feature,latlng){
        var marker = L.marker(latlng);
        marker.bindPopup(feature.properties.Location + '<br/>' + feature.properties.OPEN_DT);
        return marker;
      }
    }).addTo(map);

```

##### Add the following to call (ajax) the json file and create points to create clusters

```
$.getJSON("https://maptimeboston.github.io/leaflet-intro/rodents.geojson",function(data){
  var rodents = L.geoJson(data,{
    pointToLayer: function(feature,latlng){
      var marker = L.marker(latlng);
      marker.bindPopup(feature.properties.Location + '<br/>' + feature.properties.OPEN_DT);
      return marker;
    }
  });
  var clusters = L.markerClusterGroup();
  clusters.addLayer(rodents);
  map.addLayer(clusters);
});

```

##### add the following styles and libraries

```
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet.markercluster/1.3.0/MarkerCluster.Default.css"/>

<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet.markercluster/1.3.0/leaflet.markercluster-src.js"></script>
```
