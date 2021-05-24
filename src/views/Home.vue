<template>
  <main v-if="!loading">
    <dataTitle :title="this.title" :date="this.date" />
    <dataBoxes :stats="this.stats" />
    <selectCountry @getCountry="changeCountry" :countries="this.countries" />
    <button @click="clearCountry" v-if="this.stats.Country" class="bg-pink-700 rounded py-2 px-4 text-white hover:bg-pink-800 focus:outline-none mb-10">Clear Country</button>
  </main>
  <main v-else>
    <div class="text-grey-500 text-center text-3xl">Fetching Data</div>
    <img :src="loadingImg" class="w-24 mx-auto" alt="">
  </main>
</template>

<script>
// @ is an alias to /src
import dataTitle from '@/components/dataTitle'
import dataBoxes from '@/components/dataBoxes'
import selectCountry from '@/components/selectCountry'

export default {
  name: 'Home',
  data() {
    return {
      loading: true,
      title: 'Global',
      date: '',
      stats: {},
      countries: [],
      loadingImg: require('../assets/blue-hourglass.gif')
    }
  },
  components: {
   dataTitle,
   dataBoxes,
   selectCountry

  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      return data
    },
    changeCountry(country) {
      this.stats = country
      this.title = country.Country
    },
    async clearCountry() {
      this.loading = true
      const data = await this.fetchCovidData()
      this.title = 'Global'
      this.stats = data.Global
      // location.reload()
    }
  },
  async created() {
    const data = await this.fetchCovidData()
    console.log(data);
    this.date = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}
</script>
