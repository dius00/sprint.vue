<template>
  <div>
    <button @click="fileSelect">Upload</button>
    <input type="file" ref="input" @change="upload" />
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
      const file = this.$refs.input.files[0];
      saveObject(file);
      this.$emit("fileUploaded", file.name);
    },
  },
};
</script>

<style scope>
input {
  display: none;
}
button {
  cursor: pointer;
  margin-top: auto;
  margin-bottom: auto;
  cursor: pointer;
  font-size: 20px;
}
</style>
