<template>
  <div id="app">
    <navbar v-on:invert="changeView"/>
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ AllPhotos }}</h1>
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
    title: "CC Photo Library",
    AllPhotos: true,
    photos: [],
    selectedPhoto: ""
  }),
  methods: {
  changeView() {
    this.AllPhotos = !this.AllPhotos;
    console.log(this.AllPhotos);
  }
  }
};
</script>

<style scoped>
#app {
  text-align: center;
}
</style>
