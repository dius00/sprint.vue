<template>
  <div class="AllPhotos">
    <div v-for="(photo, index) in photos" v-bind:key="index">
      <div class="photoContainer">
        <img
          class="image"
          :src="`data:image/;base64,` + photo"
          @click="single(index)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["photos"],
  methods: {
    single(index) {
      this.$emit("singlePhotoClick", index);
    },
  },
};
</script>

<style scope>
.AllPhotos {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  flex-direction: row;
}
.photoContainer {
  position: relative;
  width: 400px;
  height: 400px;
  margin: 20px;
  overflow: hidden;
}
.photoContainer > .image {
  position: absolute;
  max-width: 100%;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.image:hover {
  cursor: pointer;
}
</style>
