<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id='map' style='width: 400px; height: 300px'></div>
  </div>
</template>

<style></style>

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
      const map = new mapboxgl.Map({
        container: 'map', // container ID
        style: 'mapbox://styles/mapbox/navigation-night-v1', // style URL
        center: [-77.11, 38.88], // starting position [lng, lat]
        zoom: 9 // starting zoom
      });
    }
    },
  };
</script>