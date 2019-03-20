<template>
  <div class="row map">
    <l-map :zoom="zoom" :center="center" @update:zoom = "zoomUpdate">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker 
        :lat-lng="latLngMethod(brew.latitude, brew.longitude)"
        v-for="(brew, index) in brews"
        :key="index"
        ></l-marker>
    </l-map>
  </div>
</template>

<script>
import {LMap, LTileLayer, LMarker } from 'vue2-leaflet';
export default {
  name: 'BrewMap',
  props: {
    brews: Array
  },
  data: function() {
    return {
      zoom:13,
      center: L.latLng(47.413220, -1.219482),
      url:'https://tile.thunderforest.com/transport/{z}/{x}/{y}.png?apikey=b5078ccdcc73457b96bafaaacf3db25f',
      attribution:'&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(47.413220, -1.219482),
    }
  },
  methods: {
    latLngMethod: function(lat, lng) {
      return L.latLng(lat, lng);
    }
  },
  components: {
      LMap,
      LTileLayer,
      LMarker
  }
}
</script>

<style>
  .map {
    height: 90vh;
  }
</style>
