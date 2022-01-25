<template>
  <body>
    <div v-if="result" class="about">
      <header>
        <h1>Clima en San Cristobal De Las Casas</h1>
      </header>
      <main class="sombra color-main">
        <div>
          <h2>Weather:</h2>
          <p>ID: {{ result.id }}</p>
          <p>Name: {{ result.name }}</p>
          <p>Visibility: {{ result.visibility }}</p>
          <p>Id: {{ result.weather[0].id }}</p>
          <p>Main: {{ result.weather[0].main }}</p>
          <p>Description: {{ result.weather[0].description }}</p>
          <p>Temp: {{ result.main.temp }}</p>

          <p>Tem-min: {{ result.main.temp_min }}</p>
          <p>Tem-max: {{ result.main.temp_max }}</p>
          <p>Humidity: {{ result.main.humidity }}</p>
          <h3 class="country">Country:</h3>
          {{ result.sys.country }}
        </div>
        <div>
          <img
            :src="'http://openweathermap.org/img/w/'+result.weather[0].icon+'.png'"
            alt="icono-clima"
          />
          
        </div>
      </main>
    </div>
  </body>
</template>
<style>
body {
  background-color: #e0d8db;
}
.sombra {
  -webkit-box-shadow: 0px 2px 21px -4px rgba(0, 0, 0, 0.85);
  -moz-box-shadow: 0px 2px 21px -4px rgba(0, 0, 0, 0.85);
  box-shadow: 0px 2px 21px -4px rgba(0, 0, 0, 0.85);
  padding: 20px;
}

.color-main {
  background-color: rgb(186, 207, 206);
}

.country__no-bold {
  font-weight: normal;
}
</style>
<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {
    axios
      .get(
        "https://api.openweathermap.org/data/2.5/weather?q=San%20Crist%C3%B3bal%20de%20las%20Casas&APPID=96c8633dd3d3a75cd5b74fd69dca0a9b"
      )
      .then((result) => {
        //console.log(result.data);
        this.result = result.data;
      });
  },
};
</script>
