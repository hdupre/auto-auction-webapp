<template>
  <div>
    <div style="margin-top: 10rem;" class="container mb-5">
      <p class="">Welcome to NYC Auto Auctions! This site is a better and faster way to explore the cars being sold at <a href="https://www.nyc.gov/site/finance/vehicles/services-auctions.page" target="_blank" rel="noopener noreferrer" class="text-blue-600">NYC impound auctions</a>.</p>
      <p class="">Not all cars will be available on auction day -- some may be claimed after the creation of this list.</p>
    </div>
    <AuctionList />
  </div>
</template>

<script>
import AuctionList from "@/components/AuctionList";
export default {
  name: "HomePage.vue",
  components: {AuctionList}
}
</script>

<style scoped>

</style>