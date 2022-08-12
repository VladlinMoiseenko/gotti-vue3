<template>

  <v-app-bar
    density="compact"
    >
    <v-app-bar-title>gotti-vue3</v-app-bar-title>
  </v-app-bar>

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
      </v-content>

<v-divider></v-divider>

      <v-footer class="text-white text-center flex-column">

         <v-card
            elevation="0"
            rounded="0"
            width="100%"
            class=" text-center">

            <v-card-text>
              <h3>Lottie анимации загруженные с сервера gotti</h3>
            </v-card-text>

            <v-card-text>
              <h3>Стек: Vue3, Vuetify, Lottie-player, Axios</h3>
            </v-card-text>

            <v-card-text>

            <v-btn flat
              variant="outlined"
              prepend-icon="mdi-github"
            >
              <a href="https://github.com/VladlinMoiseenko/gotti-vue3" target="_blank">gotti-vue3 доступен на github</a>
            </v-btn>

          </v-card-text>

          <v-card-text>
            {{ new Date().getFullYear() }} — <a href="https://vladlin.ru/" target="_blank">vladlin.ru</a>
          </v-card-text>
        </v-card>

      </v-footer>

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
