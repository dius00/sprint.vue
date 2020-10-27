<template>
  <div>
    <button @click="fileSelect">Upload</button>
    <input type="file" ref="input" @change="upload" multiple />
  </div>
</template>

<script>
import { saveObject } from "../../utils/index.js";
export default {
  name: "Upload",
  methods: {
    fileSelect() {
      this.$refs.input.click();
    },
    upload() {
      for (let i = 0; i < this.$refs.input.files.length; i++) {
        saveObject(this.$refs.input.files[i])
      console.log('here');
      }
      alert(`${this.$refs.input.files.length} file(s) uploaded`)
      this.$emit("fileUploaded");
    },
  },
};
</script>

<style scope>
input {
  display: none;
}
</style>
