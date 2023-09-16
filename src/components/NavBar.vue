<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <a class="navbar-brand" href="index.html">
        <img :src="favicon" alt="Logo" width="100">
      </a>
      <a class="navbar-brand" href="index.html">NYC Auto Auctions</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link" href="index.html">auction list</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="alerts.html">my alerts</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="about.html">about</a>
          </li>
        </ul>
        <AuthButtons />
      </div>
    </div>
  </nav>
</template>


<script>
import AuthButtons from './AuthButtons.vue'; // adjust path if necessary
export default {
  name: "NavBar",
  components: {
    AuthButtons
  },
  data() {
    return {
      favicon: require('@/assets/favicon.png')
    }
  }
}
</script>

<style scoped>

</style>