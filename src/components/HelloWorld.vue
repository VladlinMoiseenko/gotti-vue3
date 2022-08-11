<template>

  <div id="app">
    <v-app id="inspire">

      <v-content>

       <v-container fluid>
 
        <ul>
          <li v-for="item in jsondata" :key="item.id" >
            <lottie-player
              autoplay
              controls
              loop
              mode="normal"
              :src=item.animationlottie
              style="width: 320px"
            >
            </lottie-player>
          </li>
        </ul> 

        </v-container> 

      <v-container fluid>

      </v-container> 

      </v-content>
      <v-footer></v-footer>
    </v-app>
  </div>

</template>

<script>
import "@lottiefiles/lottie-player";

export default {

  name: "App",
  data() {
    return {
      jsondata: [],
    };
  },
  async mounted() {
    const { data } = await this.axios.get(
      "http://gottiserv.vladlin.ru:3001/api/gotti"
    );
    this.jsondata = data.data;
    }, 
  };
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

</style>
