<template>
  <div id="app">
    <navbar
      v-on:invert="defaultView"
      :photos="photos"
      :fullView="fullView"
      :scrollPosition="scrollPosition"
      v-on:fileUploaded="appendPhoto"
    />
    <a href="#top">Back to top</a>
    <div v-if="photos.length === 0">
      <img
        src="https://icon-library.com/images/loading-icon-animated-gif/loading-icon-animated-gif-19.jpg"
      />
    </div>
    <div v-else>
      <allPhotos
        v-if="fullView"
        :photos="photos"
        :selectedPhoto="selectedPhoto"
        :scrollPosition="scrollPosition"
        v-on:singlePhotoClick="switchView"
      />
      <singlePhoto v-else :selectedPhoto="selectedPhoto" />
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import { listObjects, getSingleObject } from "../utils/index.js";
import AllPhotos from "./components/AllPhotos";
import SinglePhoto from "./components/SinglePhoto";

export default {
  name: "App",
  components: {
    navbar: Navbar,
    allPhotos: AllPhotos,
    singlePhoto: SinglePhoto,
  },
  data: () => ({
    title: "CC Photo Library",
    fullView: true,
    photos: [],
    selectedPhoto: "",
    scrollPosition: {},
  }),
  methods: {
    defaultView() {
      this.fullView = true;
    },
    switchView(index) {
      this.fullView = false;
      this.selectedPhoto = index;
      this.scrollPosition = {x: window.scrollX, y: window.scrollY};
    },
    async appendPhoto(filename) {
      this.photos = await listObjects();
    },
  },
  created: async function() {
    this.photos = await listObjects();
  },
};
</script>

<style scoped>
#app {
  text-align: center;
  user-select: none;
}
a {
  right: 0px;
  bottom: 0px;
  font-size: 20px;
  font-family: Arial, Helvetica, sans-serif;
  position: fixed;
  color: #1c7e88;
  margin-bottom: 30px;
  margin-right: 30px;
  z-index: 2;
}
navbar {
  margin-bottom: 10px;
}
</style>
