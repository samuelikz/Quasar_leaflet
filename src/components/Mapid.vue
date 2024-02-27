<template>
  <q-page class="flex">
    <q-card style="flex:1">
      <l-map :zoom="zoom" :center="center" :mapid="'my-map-id'">
        <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
        <l-marker v-for="(position, index) in positions" :key="index" :lat-lng="position">
          <l-icon :icon-anchor="staticAnchor" class-name="someExtraClass">
            <div class="icon-wrapper">
              <img src="../assets/local.png">
              <div class="headline">{{ customTexts[index] }}</div>
            </div>
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
      positions: [
        L.latLng(-8.0622251, -34.882365),
        L.latLng(-8.0522251, -34.872365),
        L.latLng(-8.0422251, -34.862365)
      ],
      icon: L.icon({
        iconUrl: '../assets/local.png',
        iconSize: [32, 37],
        iconAnchor: [16, 37]
      }),
      staticAnchor: [16, 37],
      customTexts: ['Prefeitura', 'Escola', 'Hospital'],
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
  .icon-wrapper {
    position: relative;
    text-align: center;
  }
  .icon-wrapper img {
    display: block;
    margin: 0 auto;
  }
  .icon-wrapper .headline {
    position: absolute;
    bottom: -20px;
    left: 0;
    right: 0;
    font-size: 14px;
    font-weight: bold;
    color: black;
  }
</style>
