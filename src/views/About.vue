<template>
  <div v-if="result" class="about">
 
    <h1>Wellcome to my web page about weather</h1>

    <header>
        <p>Tis is the weathr in {{ result.name }} to day</p>
    </header>
    
    <img :src="'http://openweathermap.org/img/w/'+result.weather[0].icon+'.png'" alt=" " />
    <p>{{ result.weather[0].description }}</p>
    <p>Temperature: {{ result.main.temp }}</p>
    <p>Degrees: {{ result.wind.deg }}</p>

  </div>

</template>


<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {

      axios.get("https://api.openweathermap.org/data/2.5/weather?q=playa%20del%20carmen&APPID=36ffda36a4d355a80a24f8d3bf89024e").then((result) => {
        this.result = result.data;
        console.log(result.data);
      });
  },
};
</script>