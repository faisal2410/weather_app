<script setup>
import { useWeatherStore } from './stores/weather';

const weatherStore = useWeatherStore();

</script>

<template>

<div class="container">
  <div class="wrap">
    <!-- Search Box for Location -->
    <div class="search-box">
      <input type="text" placeholder="Search..." class="search-bar"
      v-model="weatherStore.location_query"
      @keypress="weatherStore.fetchWeather"
      >
    </div>

    <!-- Weather Information -->
    <div class="weather-info" v-if="weatherStore.weather.main !=undefined">
      <div class="location-box">
          <div class="location">{{ weatherStore.weather.name }}, {{ weatherStore.weather.sys.country }}</div>
          <div class="date">{{ new Date().toLocaleString() }}</div>
      </div>

      <div class="weather-box">
        <div class="temp">{{ weatherStore.weather.main.temp }} °c</div>
        <div class="weather">{{ weatherStore.weather.weather[0].main }}</div>
        <div class="icon">
          <img :src="`http://openweathermap.org/img/wn/${weatherStore.weather.weather[0].icon}@2x.png`" alt="">
        </div>
        <div class="other-info">
          <span class="pressure">Pressure: {{ weatherStore.weather.main.pressure }} mb</span>
          <span class="pressure">Humidity: {{ weatherStore.weather.main.humidity }} %</span>
        </div>
      </div>
    </div>
  </div>
</div>

</template>

<style scoped>


</style>