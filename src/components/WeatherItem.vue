<template lang="html">
  <li>
    <article class="">
      <img :src=" 'https://www.metaweather.com/static/img/weather/' + day.weather_state_abbr + '.svg' " alt="weather state" width="30" class="weather-picture"><br>
      <p>{{day.max_temp.toFixed(0)}}°C </p>
      <p><span class="min-temp"> {{day.min_temp.toFixed(0)}}°C</span></p>
    </article>
  </li>
</template>

<script>
export default {
  name: "WeatherItem",
  props: ["day"]
}
</script>

<style lang="css" scoped>

  li{
    font-size: 0.9em;
    list-style: none;
    height: 50px;
  }

  .min-temp{
    color: #BBBBBB;
  }
  p{
    display: inline-block;
    padding-right: 5px;
    padding-left: 5px;
  }


</style>
