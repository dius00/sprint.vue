<template>
  <div>
    <img :src="`data:image/;base64,` + image">
  </div>
</template>

<script>
export default {
  name: "SinglePhoto",
  props: ["image"],
};
</script>

<style></style>
