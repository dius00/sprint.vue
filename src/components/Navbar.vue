<template>
<div id="navbar">
  <h1 id="navbar-header">Go Home</h1>
</div>
</template>

<script>
export default {
  name: "Navbar"
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
