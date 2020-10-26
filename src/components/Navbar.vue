<template>
<div id="navbar">
  <h1 id="navbar-header" @click="changeView">Go Home</h1>
  <upload/>
</div>
</template>

<script>
import Upload from "./Upload"
export default {
  name: "Navbar",
  components: {
    upload: Upload
  },
  props: ["value"],
  methods: {
  changeView() {
    this.$emit("invert");
    /*this.AllPhotos = !this.AllPhotos;
    console.log(this.AllPhotos);*/
  }
  }
};
</script>

<style scoped>
#navbar-header {
  cursor: pointer;
  margin-top: auto;
  margin-bottom: auto;
  margin-right: auto;
}
#navbar {
  padding: 2rem;
  display: flex;
  justify-content: flex-end;
  background-color: #1c7e88;
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(255, 255, 255);
}
</style>
