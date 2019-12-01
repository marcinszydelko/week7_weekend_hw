<template>
  <div id="app">
    <h1>WeatherApp</h1>
    <input v-model="search" @input="searchHandler" type="text" placeholder="Search for city">
    <CitiesList v-bind:cities="cities" />
  </div>
</template>

<script>
import CitiesList from './components/CitiesList.vue'

export default {
  data(){
    return {
      cities: [],
      search: ""
    }
  },
  name: 'app',
  components: {
    CitiesList
  },
  methods: {
    searchHandler() {
      if (this.search.length > 2){
        return fetch(`https://cors-anywhere.herokuapp.com/https://www.metaweather.com/api/location/search/?query=${this.search}`)
        .then(res => res.json())
        .then(cities => this.cities = cities)
      }else{
        return this.cities = []
      }
    }

  }
}

</script>

<style>

</style>
