<template>
  <div id="app">
    <h1>WeatherApp</h1>

    <div id="wrapper">
      <div class="element">
        <label for="searchForCity">Search for city:</label><br>
        <input v-model="search" @input="searchHandler" type="text" placeholder="type at least 3 letters" id="searchForCity" width="200">
        <CitiesList v-bind:cities="cities" />
      </div>

      <div class="element">
        <WeatherInfo/>
      </div>

    </div>
  </div>
</template>

<script>
import CitiesList from './components/CitiesList.vue'
import WeatherInfo from './components/WeatherInfo.vue'

export default {
  data(){
    return {
      cities: [],
      search: "",
      selectedCity: []
    }
  },
  name: 'app',
  components: {
    CitiesList,
    WeatherInfo
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
  #wrapper{
    display: flex;
    justify-content: space-evenly;
  }

  .element{
    flex-direction: row;
  }

</style>
