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
export default {
  name: "Navbar",
  components: {
    upload: Upload,
  },
  methods: {
    invert() {
      this.$emit("invert");
    },
  },
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
</style>
