<template lang="html">
  <div class="weather-display">
    <h2>{{city.title}}, {{city.parent.title}}</h2>
    <div id="weather-box">
      <div class="weather-readings" id="box-left">
        <img :src=" 'https://www.metaweather.com/static/img/weather/' + city.consolidated_weather[0].weather_state_abbr + '.svg' " alt="weather state" width="40" class="weather-picture">
        <p class="temp">{{city.consolidated_weather[0].the_temp}}°C</p>
      </div>
      <div class="weather-readings" id="right-box">
        <p>Humidity: {{city.consolidated_weather[0].humidity}}%</p>
        <p>Wind: {{city.consolidated_weather[0].wind_speed}} mph</p>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  name: "WeatherInfo",
  props: ['city']
}
</script>

<style lang="css" scoped>
.weather-display{
  border: 1px solid black;
  padding: 10px 30px;
  width: 500px;
  border-radius: 5px;
}

#weather-box{
display: flex;
}

.weather-readings{
  flex-direction: row;
  border: 1px solid black;
}
#box-left{
  margin-right: 150px;
  display: flex;
}
img.#box-left{
  margin-right: 20px;
}

.temp{
  font-size: 2em;
}

.weather-picture{
  margin-right: 20px;
}

</style>
