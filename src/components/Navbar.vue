<template>
  <div id="navbar">
    <h1 id="navbar-header" @click="invert">Go Home</h1>
    <img
      class="topLogo"
      src="https://pbs.twimg.com/profile_images/1281073106711310337/lJkvgoyy_400x400.png"
    />
    <h2 class="topTitle">CC Photo Library</h2>
    <upload v-on="$listeners" />
  </div>
</template>

<script>
import Upload from "./Upload";
import { listObjects } from "../../utils/index.js";
export default {
  name: "Navbar",
  components: {
    upload: Upload,
  },
  props: ["photos", "fullview", "scrollPosition"],
  methods: {
    invert() {
      listObjects().then((data) => {
        this.photos = data;
        this.fullView = false;
        this.fullView = true;
        console.log(this.scrollPosition);
        window.scrollTo(this.scrollPosition.x, this.scrollPosition.y);
      });
      this.$emit("invert", this.photos, this.fullView, this.scrollPosition);
    },
  },
};
</script>

<style >
#navbar-header {
  cursor: pointer;
  margin-top: auto;
  margin-bottom: auto;
  margin-right: auto;
}
#navbar {
  padding: 2rem;
  position: relative;
  display: flex;
  background-color: #1c7e88;
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(255, 255, 255);
}
.topLogo {
  margin-top: auto;
  display: flex;
  height: 100px;
}

.topTitle {
  display: inline;
  margin-right: auto;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 35px;
}

button {
  position: absolute;
  cursor: pointer;
  font-size: 20px;
  top: 50%;
  left: 93%;
  transform: translate(-50%,-50%);
}
</style>
