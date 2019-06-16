<template>
  <div style="display:inline-block; width:39%">
    <span style="color:white">Today</span> &nbsp;
    <span style="color:white; float: right; font-size:16px">
      <b>{{currentResult.main.temp}}&#8451;</b>
      <br>
      <span style="font-size:10px; color:grey">
        min: {{currentResult.main.temp_min}}&#8451;
        <br>
        max: {{currentResult.main.temp_max}}&#8451;
        <br>
      </span>
    </span>
    <br>
    <img :src="getImage">
    <br>

    <span>{{currentResult.weather[0].main}}</span>

    <br>
    Humidity : {{currentResult.main.humidity}}%
    <br>
    Wind: {{currentResult.wind.speed}}mph
    <br>
    Pressure: {{currentResult.main.pressure}} hpa
  </div>
</template>

<script>
export default {
  props: {
    currentResult: { type: Object }
  },
  computed: {
    getImage() {
      return (
        "http://openweathermap.org/img/w/" +
        this.currentResult.weather[0].icon +
        ".png"
      );
    },
  },
};
</script>

<style>
</style>