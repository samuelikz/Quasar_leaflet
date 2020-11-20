<template>
  <q-page class="flex">
    <q-card style="flex:1">
      <l-map :zoom="zoom" :center="center">
        <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
        <l-marker :lat-lng="marker">
          <l-icon
            :icon-anchor="staticAnchor"
            class-name="someExtraClass">
            <div class="headline">{{customText}}</div>
            <img src="../assets/local.png">
          </l-icon>
        </l-marker>
      </l-map>
    </q-card>
  </q-page>
</template>

<script>
import { LMap, LTileLayer, LMarker, LIcon } from 'vue2-leaflet'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'

export default {
  name: 'Map',
  components: {
    LMap,
    LTileLayer,
    LMarker,
    LIcon
  },
  data () {
    return {
      zoom: 11,
      center: L.latLng(-8.0429475, -35.0743063),
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(-8.0622251, -34.882365),
      icon: L.icon({
        iconUrl: '../assets/local.png',
        iconSize: [32, 37],
        iconAnchor: [16, 37]
      }),
      staticAnchor: [16, 37],
      customText: 'Fulano',
      iconSize: 64
    }
  }
}
</script>

<style lang="stylus" scoped>
  .q-card{
    width: 100%;
    height auto;
  }
</style>
