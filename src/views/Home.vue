<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id='map' style='width: 400px; height: 300px'></div>
  </div>
</template>
 
<style>
#marker {
background-image: url('https://docs.mapbox.com/mapbox-gl-js/assets/washington-monument.jpg');
background-size: cover;
width: 50px;
height: 50px;
border-radius: 50%;
cursor: pointer;
}
 
.mapboxgl-popup {
max-width: 200px;
}
</style>

<script>
import mapboxgl from 'mapbox-gl'; // or "const mapboxgl = require('mapbox-gl');"

  export default {
    data: function () {
      return {
        message: "Welcome to Vue.js!",
        map: []
      };
    },
    mounted: function () {
      this.generateMap();
    },
    methods: {
      generateMap: function() {
      mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_KEY;
      const monument = [-77.0353, 38.8895];
      const map = new mapboxgl.Map({
        container: 'map', // container ID
        style: 'mapbox://styles/mapbox/navigation-night-v1', // style URL
        center: [-77.11, 38.88], // starting position [lng, lat]
        zoom: 8 // starting zoom
      });
      const marker1 = new mapboxgl.Marker({ color: 'black', rotation: 45 })
        .setLngLat([-77.05294, 38.53539])
        .addTo(map);
      const marker2 = new mapboxgl.Marker({ color: 'black', rotation: 45 })
        .setLngLat([-77.10541, 38.88582])
        .addTo(map);
      const popup = new mapboxgl.Popup({ offset: 25 }).setText(
        'Construction on the Washington Monument began in 1848.'
      );
      const el = document.createElement('div');
        el.id = 'marker';
      new mapboxgl.Marker(el)
        .setLngLat(monument)
        .setPopup(popup) // sets a popup on this marker
        .addTo(map);
    }
    },
  };
</script>