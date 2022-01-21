<template>
  <div class="flex flex-col h-screen max-h-screen">
    <!-- Search/Result -->
    <div class="z-20 flex justify-center relative bg-hero-pattern bg-cover px-2 pt-8 pb-32">
      <!-- Search input -->
      <div class="w-full max-w-screen-sm">
        <h1 class="text text-center text-white text-3xl pb-4">IP Address Tracker</h1>
        <div class="flex">
          <input class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none" type="text" placeholder="Search for any IP address or leave empty to get your IP info">
          <i class="
          cursor-pointer
          bg-black
          text-white
          px-4
          flex
          items-center
          rounded-tr-md
          rounded-br-md
          fas fa-chevron-right"></i>
        </div>
      </div>
      <!-- Search Result -->
      <IPInfo/>
    </div>
    <!-- Map -->
    <div id="mapid" class="h-full z-10"></div>

  </div>
</template>

<script>

import { onMounted } from 'vue'
import IPInfo from '../components/IPInfo.vue'
import leaflet from 'leaflet'
export default {
  name: 'Home',
  components: {
    IPInfo
  },
  setup() {
    let myMap;
    onMounted(()=>{
      myMap = leaflet.map('mapid').setView([51.505, -0.09], 13);
      leaflet.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1Ijoic2Fsc2NvZGVzIiwiYSI6ImNreW8wMTc1NTJtbzEyb3AwODZpYjhhZDgifQ.i42mc7jKGhBqh-GvcAvXRA', {
        attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
        maxZoom: 18,
        id: 'mapbox/streets-v11',
        tileSize: 512,
        zoomOffset: -1,
        accessToken: 'pk.eyJ1Ijoic2Fsc2NvZGVzIiwiYSI6ImNreW8wMTc1NTJtbzEyb3AwODZpYjhhZDgifQ.i42mc7jKGhBqh-GvcAvXRA'
      }).addTo(myMap);
    })
  }
}

// 3070009137
// NAFIU ISAH

</script>
