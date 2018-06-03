
<template>
  <div>
    <no-ssr>
      <div id="mapid" style="height: 100%; width: 900px; height: 400px;">
          <v-map :zoom="zoom" :center="center">
              <v-tilelayer :url="url" :attribution="attribution"></v-tilelayer>
              <v-marker :lat-lng="marker"></v-marker>
          </v-map>
      </div>
    </no-ssr>
  </div>
</template>

<script>
import L from 'leaflet'
import Vue2Leaflet from 'vue2-leaflet'

if (process.browser) {
  console.log('browser.process haut: ' + process.browser)
} else {
  console.log('browser.process bas: ' + process.browser)
}

// import { L } from 'leaflet'
export default {
  layout: 'default',
  head: {
    link: [
      {
        rel: 'stylesheet',
        href: 'https://unpkg.com/leaflet@1.0.3/dist/leaflet.css'
      }
    ]
  },
  components: {
    'v-map': Vue2Leaflet.LMap,
    'v-tilelayer': Vue2Leaflet.LTileLayer,
    'v-marker': Vue2Leaflet.LMarker
  },
  data () {
    return {
      zoom: 13,
      center: L.latLng(47.413220, -1.219482),
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(47.413220, -1.219482)
    }
  },
  mounted () {
  }
}
</script>

<style>

</style>
