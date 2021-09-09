<template>
  <div class="home">
    <h1>Hello World</h1>
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {
    
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    }
  },
  created() {
    console.log()
  }
}
</script>
