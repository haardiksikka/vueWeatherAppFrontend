<template>
  <div class="hello">
    <form action>
      <input class="homeBody" type="text" v-model="city" placeholder="Enter City">

      <i class="fa fa-search" @click="getWeatherInfo()"></i>
    </form>

    <div class="row" style="text-align:left" v-show="currentWeather!=null">
      <div class="col widget-block">
        <h3 style="color:white; text-transform: capitalize">{{theCity}}'s Current Weather</h3>
        <hr>
        <CurrentWeather :currentResult="currentWeather"></CurrentWeather>
        <h3 style="color:white; text-transform: capitalize">{{theCity}}'s Weather Forecast</h3>
        <hr>
      </div>
      <div class="col-sm-2 widget-block" v-for="(item,index) in weatherArray" :key="index">
        <WeatherData :weatherdata="item"></WeatherData>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import WeatherData from '../weather/weather.vue';
import CurrentWeather from '../currentweather/currentweather.vue';

export default {
  name: 'HomePage',
  components: {
    WeatherData,
    CurrentWeather,
  },
  data() {
    return {
      theCity: '',
      posts: {},
      errors: {},
      weatherArray: [],
      currentWeather: null,
      city: '',
    };
  },

  methods: {
    async getWeatherInfo() {
      try {
        const result = await axios.get(
          `//api.openweathermap.org/data/2.5/forecast?q=${
            this.city
          }&units=metric&APPID=5d0eb2eb209b8c9339fc37663921e74c`
        );
        const current = await axios.get(
          `//api.openweathermap.org/data/2.5/weather?q=${
            this.city
          }&units=metric&APPID=5d0eb2eb209b8c9339fc37663921e74c`
        );
        this.currentWeather = current.data;
        for (let i = 0; i < result.data.list.length;) {
          this.weatherArray.push(result.data.list[i]);
          i += 8;
        }
        this.theCity = this.city;
      } catch (err) {
        console.log(err);
        this.weatherArray = [];
        this.currentWeather = null;
        alert('location not found');
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.widget {
  background-color: rgba(0, 0, 0, 0.7);
  border-radius: 16px;
  margin-top: 34px;
}

.widget-block {
  color: grey;
  padding: 15px;
  display: block;
}

.homeBody {
  padding: 10px;
  margin: 0;
  width: 100%;
  background: white;
}

form {
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: all 1s;
  width: 50px;
  height: 50px;
  background: white;
  box-sizing: border-box;
  border-radius: 25px;
  border: 4px solid white;
  padding: 5px;
}

input {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 42.5px;
  line-height: 30px;
  outline: 0;
  border: 0;
  display: none;
  font-size: 1em;
  border-radius: 20px;
  padding: 0 20px;
}

.fa {
  box-sizing: border-box;
  padding: 10px;
  width: 42.5px;
  height: 42.5px;
  position: absolute;
  top: 0;
  right: 0;
  border-radius: 50%;
  color: #07051a;
  text-align: center;
  font-size: 1.2em;
  transition: all 1s;
}

form:hover {
  width: 200px;
  cursor: pointer;
}

form:hover input {
  display: block;
}

form:hover .fa {
  background: #07051a;
  color: white;
}
</style>
