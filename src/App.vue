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
        <WeatherInfo v-bind:city="selectedCity"/>
      </div>

    </div>
  </div>
</template>

<script>
import CitiesList from './components/CitiesList.vue'
import WeatherInfo from './components/WeatherInfo.vue'
import { eventBus } from './main.js'

export default {
  data(){
    return {
      cities: [],
      search: "",
      selectedCity: null,
      weatherOfCity: []
    }
  },
  name: 'app',
  components: {
    CitiesList,
    WeatherInfo
  },
  mounted(){
    fetch(`https://cors-anywhere.herokuapp.com/https://www.metaweather.com/api/location/44418`)
    .then(res => res.json())
    .then(city => this.selectedCity = city)

    eventBus.$on('city-selected', (city) => {
      this.selectedCity = city
    })
  },
  methods: {
    searchHandler() {
      if (this.search.length > 2){
        return fetch(`https://cors-anywhere.herokuapp.com/https://www.metaweather.com/api/location/search/?query=${this.search}`)
        .then(res => res.json())
        .then(cities => this.cities = cities)
      }else {
        return this.cities = []
      }
    },


  }
}

</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Solway&display=swap');
  h1{
    font-family: 'Solway', serif;
    text-align: center;
    margin: 0 auto;
    margin-bottom: 30px;
    padding: 20px 0 40px;
    background-color: #D4D4D4;
  }

  #wrapper{
    display: flex;
    justify-content: space-evenly;
  }

  .element{
    flex-direction: row;
  }
  body{
    margin: 0;
  }

</style>
