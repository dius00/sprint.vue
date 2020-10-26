<template>
  <div class="singleFrame">
    <img class="singleImage" :src="`data:image/;base64,` + image" />
  </div>
</template>

<script>
export default {
  name: "SinglePhoto",
  props: ["image"],
};
</script>

<style scope>
.singleFrame {
  position: relative;
  max-width: 100%;
}

.singleImage {
  padding-top: 20px;
  padding-left: 1cm;
  padding-right: 1cm;
  position: absolute;
  max-width: 100%;
  left: 50%;
  transform: translateX(-50%);
  cursor: pointer;
}
</style>
