<template>
  <v-container>
  <h2>VueAxios demo</h2>
  <ul>
    <li v-for="user in users" :key="user.id">{{ user.name }}</li>
  </ul>
  </v-container>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      users: [],
    };
  },
  async mounted() {
    const { data } = await this.axios.get(
      "https://jsonplaceholder.typicode.com/users"
    );
    this.users = data;
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
</style>