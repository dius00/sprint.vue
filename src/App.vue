<template>
  <div id="app">
    <navbar v-on:invert="defaultView" v-on:fileUploaded="appendPhoto"/>
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ fullView }}</h1>
    <allPhotos v-if="fullView" :photos="photos" v-on:singlePhotoClick ="switchView"/>
    <singlePhoto v-else :image="photos[selectedPhoto]"/>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import {listObjects, getSingleObject} from  "../utils/index.js"
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
    selectedPhoto: -1,
  }),
  methods: {
  defaultView() {
    this.fullView = true;
  },
  switchView(index) {
    this.fullView = false;
    this.selectedPhoto = index;
  }, 
  async appendPhoto(filename) {
    this.photos.push(await getSingleObject(filename));
  }},
  created: async function() {
   const list = (await listObjects()).map(file => file.Key);
   for (let key of list) {
     this.photos.push(await getSingleObject(key))
   }
  },
};
</script>

<style scoped>
#app {
  text-align: center;
}
</style>
