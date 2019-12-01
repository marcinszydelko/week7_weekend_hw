<template lang="html">
  <div class="weather-display">
    <h2>{{city.title}}, {{city.parent.title}}</h2>
    <h5>{{city.consolidated_weather[0].applicable_date}}</h5>
    <div id="weather-box">
      <div class="weather-readings" id="box-left">
        <img :src=" 'https://www.metaweather.com/static/img/weather/' + city.consolidated_weather[0].weather_state_abbr + '.svg' " alt="weather state" width="45" class="weather-picture">
        <p class="temp">{{city.consolidated_weather[0].the_temp.toFixed(0)}}°C</p>
      </div>
      <div class="weather-readings" id="right-box">
        <p>Humidity: {{city.consolidated_weather[0].humidity}}%</p>
        <p>Wind direction:  {{city.consolidated_weather[0].wind_direction_compass}}</p>
        <p>Wind: {{city.consolidated_weather[0].wind_speed.toFixed(2)}} mph</p>
      </div>
    </div>
    <div id="next-days">
      <ul v-for="day in city.consolidated_weather.slice(1, 6)">
        <WeatherItem v-bind:day="day" />
      </ul>
    </div>

  </div>

</template>

<script>
import WeatherItem from './WeatherItem.vue'


export default {
  name: "WeatherInfo",
  props: ['city'],
  components: {
    WeatherItem
  }
}
</script>

<style lang="css" scoped>
.weather-display{
  border: 1px solid black;
  padding: 10px 30px;
  width: 500px;
  height: 400px;
  border-radius: 5px;
}

#weather-box{
display: flex;
}

.weather-readings{
  flex-direction: row;

}
#box-left{
  margin-right: 150px;
  display: flex;
}
img.#box-left{
  margin-right: 20px;
}

.temp{
  font-size: 3em;
}

.weather-picture{
  margin-right: 20px;
}

#next-days{
  display: flex;
  flex-direction: row;
  flex-wrap: no-wrap;
  margin-top: 0px;
  justify-content: space-around;

}

ul{
  padding-left: 0px;
}


</style>
