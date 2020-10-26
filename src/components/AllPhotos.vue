<template>
  <div class="AllPhotos">
    <div v-for="(photo, index) in photos" v-bind:key="index">
      <div class="photoContainer">
        <img
          class="image"
          :src="`https://s3-ap-northeast-1.amazonaws.com/react.sprint/` + photo"
          @click="single(photo)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["photos",
  "selectedPhoto",
  "fullView"],
  methods: {
    single(photo) {
      this.selectedPhoto = photo
      this.fullView = false
      this.$emit("singlePhotoClick", this.selectedPhoto, this.fullView);
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
