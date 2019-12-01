<template lang="html">
  <div>
    <li @click="handleClickCity" >{{city.title}}</li>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: "CitiesItem",
  props: ["city"],
  methods: {
    handleClickCity() {
        fetch(`https://cors-anywhere.herokuapp.com/https://www.metaweather.com/api/location/${this.city.woeid}`)
        .then(res => res.json())
        .then(city =>  eventBus.$emit('city-selected', city ))

    }
  }
}
</script>

<style lang="css" scoped>
</style>
