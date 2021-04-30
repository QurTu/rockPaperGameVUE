<template>
  <div class="weather-block">
    <p v-if="error == true"> sorry something went wrong. Can`t display weather information</p>
    <h1 v-if="error == false">{{city}}</h1>
    <p v-if="error == false">{{ "Temp: " + temp + 'C' }}</p>
    <p v-if="error == false">{{"Feels like: " + feltTemp + 'C'}}</p>
  </div>
</template>

<script>
export default {
  name: "WeatherShow",
  data() {
    return {
      city: '',
      temp: '',
      feltTemp: '',
      error:false,

    }
  },
  methods: {
    getWeatherInfo() {
      const key = "f5bfb48c799acb18734e01392cc425d7"
      window.addEventListener('load', () => {
        let lon;
        let lat;
        if (navigator.geolocation) {
          navigator.geolocation.getCurrentPosition(position => {
            lon = position.coords.longitude;
            lat = position.coords.latitude;
            let API = `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&units=metric&appid=${key}`;

            fetch(API)
                .then(Response => {
                  if(Response.ok) {
                    return Response.json();
                  }
                  else {
                    this.error = true;
                  }

                })
                .then(data => {

                  console.log(data);
                  this.city = data.name;
                  this.temp =  parseFloat( data.main.temp).toFixed(1);
                  this.feltTemp = parseFloat( data.main.feels_like).toFixed(1);
                }).catch(error => {
                  console.log(error)
                  this.error = true;

            })
          })
        }
      });

    }

  },
  mounted() {
    this.getWeatherInfo();
  }
}

</script>

<style scoped>
.weather-block {
  color: #fff;
  text-align: center;
  position: absolute;
  bottom: 20px;
  right: 20px;
  border: 2px solid #fff;
  padding: 20px;
}
h1 {
  padding-bottom: 10px;
}
p {
  padding: 5px;
}


</style>