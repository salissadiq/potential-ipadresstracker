<template>
  <div class="absolute
    -bottom-64
    lg:-bottom-20
    flex
    flex-col
    lg:flex-row
    bg-white
    gap-y-4
    gap-x-12
    px-8 pt-8 py-12
    rounded-md
  ">
    <!-- Flex Item 1 -->
    <div class="flex flex-col">
        <h1 class=" text-xs mb-2 uppercase">IP Address</h1>
        <span class="text-2xl">8.8.8.8</span>
    </div>

     <!-- Flex Item 2 -->
    <div class="flex flex-col">
        <h1 class=" text-xs mb-2 uppercase">Location</h1>
        <span class="text-2xl">Silicon Valley</span>
    </div>


     <!-- Flex Item 3 -->
    <div class="flex flex-col">
        <h1 class=" text-xs mb-2 uppercase">Timezone</h1>
        <span class="text-2xl">UTC +9:03</span>
    </div>
     <!-- Flex Item 4 -->
    <div class="flex flex-col">
        <h1 class=" text-xs mb-2 uppercase">ISP</h1>
        <span class="text-2xl">Google Inc</span>
    </div>
  </div>
</template>

<script>
export default {

}
</script>