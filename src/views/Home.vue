<template>
  <div class="flex flex-col h-screen max-h-screen">
    <!-- Search/Result -->
    <div class="z-20 flex justify-center relative bg-hero-pattern bg-cover px-2 pt-8 pb-32">
      <!-- Search input -->
      <div class="w-full max-w-screen-sm">
        <h1 class="text text-center text-white text-3xl pb-4">IP Address Tracker</h1>
        <div class="flex">
          <input 
          v-model="queryIp"
          class="flex-1 
          py-3 px-2 
          rounded-tl-md rounded-bl-md 
          focus:outline-none"
          type="text" placeholder="Search for any IP address or leave empty to get your IP info">
          <i
          @click="getIpInfo" 
          class="
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
      <IPInfo v-if="ipInfo" :ipInfo="ipInfo" />
    </div>
    <!-- Map -->
    <div id="mapid" class="h-full z-10"></div>

  </div>
</template>

<script>

import { onMounted, ref } from 'vue'
import IPInfo from '../components/IPInfo.vue'
import leaflet from 'leaflet'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    IPInfo
  },
  setup() {
    let myMap;
    const queryIp = ref("")
    const ipInfo = ref(null)
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

    const getIpInfo = async () => {
      try {
        const data = await axios.get(`https://geo.ipify.org/api/v2/country,city?apiKey=at_FHmifZsdVxhJVx5It5qODuhy9QvyB&ipAddress=${queryIp.value}`)
        const result = data.data
        ipInfo.value = {
          address: result.ip,
          state: result.location.region,
          country: result.location.country,
          timezone: result.location.timezone,
          isp: result.isp,
          lat: result.location.lat,
          lng: result.location.lng
        }
      } catch(err) {
        alert(err.message)
      }
    }

    return {queryIp, ipInfo, getIpInfo}

  }

  
}

// 3070009137
// NAFIU ISAH

</script>
