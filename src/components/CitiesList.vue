<template>
  <div>
    <ul >
      <CitiesItem v-bind:city="city" v-bind:key="index" v-for="(city, index) in cities"/>
    </ul>
  </div>

</template>

<script>
import CitiesItem from './CitiesItem.vue'

export default {
  name: 'CitiesList',
  components: {
    CitiesItem
  },
  props: ["cities"]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  ul{
    padding-left: 0;
    text-align: center;
    list-style: none;
  }

</style>
