<template>
  <p>
    <span style="color:white">{{getData}}</span>
    <br>
    {{weatherdata.weather[0].main}}
    <br>
    <img :src="getImage">
    <br>
    Temperature: {{weatherdata.main.temp}}&#8451;
    <br>
    Humidity : {{weatherdata.main.humidity}}%
  </p>
</template>
<script>
export default {
  props: {
    weatherdata: { type: Object }
  },
  computed: {
    getImage() {
      return (
        'http://openweathermap.org/img/w/' +
        this.weatherdata.weather[0].icon +
        '.png'
      );
    },
    getData() {
      return this.weatherdata.dt_txt;
    }
  }
};
</script>

<style>

</style>