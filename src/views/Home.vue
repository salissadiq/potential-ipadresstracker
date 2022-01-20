<template>
  <div class="flex flex-col h-screen max-h-screen">
    <!-- Search/Result -->
    <div class="flex justify-center relative bg-hero-pattern bg-cover px-2 pt-8 pb-32">
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
  </div>
</template>

<script>
// @ is an alias to /src

import IPInfo from '../components/IPInfo.vue'
export default {
  name: 'Home',
  components: {
    IPInfo
  }
}

// 3070009137
// NAFIU ISAH

</script>
