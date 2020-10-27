<template>
  <div class="AllPhotos">
    <div v-for="(photo, index) in photos" v-bind:key="index">
      <div class="photoContainer">
        <img
          class="image"
          :src="`https://s3-ap-northeast-1.amazonaws.com/react.sprint/` + photo.Key"
          :alt="photo.Key"
          @click="single(photo)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["photos", "selectedPhoto", "scrollPosition"],
  methods: {
    single(photo) {
      this.selectedPhoto = photo;
      this.scrollPosition = {x: window.scrollX, y: window.scrollY}
      console.log(this.scrollPosition)
      this.$emit("singlePhotoClick", this.selectedPhoto, this.scrollPosition);
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
  transition: transform .2s; /* Animation */
  overflow: hidden;
}
.photoContainer:hover {
  transform: scale(1.2);
}

.photoContainer > .image {
  position: absolute;
  max-width: 100%;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);

}
.image:hover {
  cursor: zoom-in;
}
</style>
