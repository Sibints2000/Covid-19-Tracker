<template>
  <main v-if="!loading">
    <h1>Hello World</h1>
  </main>
</template>

<script>

export default {
  name: 'Home',
  components: {},
  data(){
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif')
    }
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    }
  },
  async created() {
    const data = await this.fetchCovidData()
    
    this.dataDate = data.Date
    this.stats = data.global
    this.countries = data.Countries
    this.loading = false
  },
}
</script>
