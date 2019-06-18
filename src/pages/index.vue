<template>
  <div class="home">
    <h1>Welcome to a VueCLI Static Site with Data from an Express API</h1>
    <h2>
      Deployed with
      <a href="https://zeit.co/docs" target="_blank" rel="noreferrer noopener">ZEIT Now</a>!
    </h2>
    <br>
    <HelloExpress/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloExpress from '@/components/HelloExpress.vue'

export default {
  name: 'home',
  components: {
    HelloExpress
  }
}
</script>

<style>
  @import "../assets/style.css";
</style>