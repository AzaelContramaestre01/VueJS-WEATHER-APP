<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 15 ? 'warm' : ''">
    <main>
      <div class="search-box">
        <input type="text" 
        name="" id="" 
        class="search-bar" 
        placeholder="Search. . ."
        v-model="query"
        @keypress="fetchWeather"
        />
      </div>
      <div class="weather-wrap" v-if="typeof weather.main !='undefined'">
        <div class="location-box">
          <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
          <div class="date">{{ dateBuilder() }}</div>
        </div>
        <div class="weather-box">
          <div class="temp">{{ Math.round(weather.main.temp) }}°c</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      api_key: "6a64252f5aa08424a201683d80a09439",
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: '',
      weather: {}

    }
  },
  methods: {
    fetchWeather (e) {
      if (e.key == "Enter"){
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
        .then(res => {
          return res.json();
        }).then(this.setResults);
      }
    },
    setResults(results){
      this.weather = results;
    },
    dateBuilder () {
      let d = new Date();
      let months = [
      "January", 
      "February", 
      "March", 
      "April" , 
      "May", 
      "June", 
      "July", 
      "August", 
      "September", 
      "October", 
      "November", 
      "December"];


      let days = [
      "Sunday",
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()]
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;

    }
  }
}

</script>

<style>


*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}

#app {
  background-image: url(./assets/ice.jpg);
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm {
  background-image: url('./assets/fire.jpg');
}

main {
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75)) ;
}

.search-box{
  width: 100%;
  margin: 0 0 75px;
}

.search-box .search-bar {
 display: block;
  width: 100%;
  padding: 15px;

  appearance: none;
  background: none;
  border: none;
  outline: none;

  background-color: rgba(255,255,255,0.5);
  border-radius: 0px 0px 16px 16px;
  margin-top: -25px; 

  box-shadow: 0px 5px rgba(0,0,0,0.2);
  color: #313131;

  transition:0.4s ease;
}

.search-bar .search-box:focus{
  background-color: rgba(255,255,255,0.75);
  box-shadow: 0px 0px 16px rgba(0,0,0,0.25);
}


.location-box .location {
  color: #FFF;
  font-size: 65px;
  font-weight: 500;
  text-align: center;
  text-shadow: 3px 3px rgb(50, 50, 70, 0.5);
}

.location-box .date {
   color: #FFF;
  font-size: 28px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
  text-shadow: 2px 2px rgb(50, 50, 70, 0.5);
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
   position: relative;
  display: inline-block;
  margin: 30px auto;
  background-color: rgb(255, 255, 255, 0.2);
  border-radius: 16px;

  padding: 15px 25px;

  color: #FFF;
  font-size: 120px;
  font-weight: 900;

  text-shadow: 3px 6px rgb(50, 50, 70, 0.5);
  text-align: center;
  box-shadow: 3px 6px rgba(0,0,0,0.2);
}

.weather-box .weather{
    color: #FFF;
  font-size: 48px;
  font-weight: 700;
  text-shadow: 3px 3px rgb(50, 50, 70, 0.5);
}
</style>
