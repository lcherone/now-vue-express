<template>
  <div class="hello-express">
    <h3>The date according to Express is:</h3>
    <p>{{ date || 'Loading date...' }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloExpress',
  data() {
    return {
      date: ''
    }
  },
  created() {
    this.getDate()
  },
  methods: {
    getDate() {
      fetch('/api/date.js').then(response => response.text()).then(date => {
        this.date = date;
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
