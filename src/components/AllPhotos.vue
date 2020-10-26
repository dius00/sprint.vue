<template>
<div>
  <div v-for="(photo, index) in photos" v-bind:key="index">
    <div class="photoContainer" >
      <img :src="`data:image/;base64,` + photo"
      @click="single(index)">
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["photos"],
  methods: {
    single(index){
      this.$emit("singlePhotoClick", index)
    }
  }
};
</script>

<style>
.photoContainer {
  display: inline;
  cursor: pointer;
  }
</style>
