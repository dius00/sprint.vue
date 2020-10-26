<template>
<div>
 <button @click="upload">Upload</button>
 <input type="file" ref="input"/>
 </div>
</template>

<script>
import {saveObject} from "../../utils/index.js"
export default {
  name: "Upload",
  methods: {
  upload(){
    this.$refs.input.click();
    const file = this.$refs.input.files[0];
    console.log(file);
    }
  }
};
</script>

<style scope>

</style>
