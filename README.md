# leaflet_tutorial
Leaflet Tutorial

##### add the following javascript call


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
