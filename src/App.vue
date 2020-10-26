<template>
  <div id="app">
    <navbar />
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";

export default {
  name: "App",
  components: {
    navbar: Navbar
  },
  data: () => ({
    title: "CC Photo Library"
  })
};
</script>

<style scoped>
/* #app {
  text-align: center;
} */
</style>
