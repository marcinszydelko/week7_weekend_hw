<template>
  <div>
    <ul v-bind:key="city.woeid" v-for="city in cities">
      <CitiesItem v-bind:city="city" />
    </ul>
  </div>

</template>

<script>
import CitiesItem from './CitiesItem.vue'

export default {
  name: 'Cities',
  components: {
    CitiesItem
  },
  props: ["cities"]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
