<template>
  <el-input class="input" v-model="input" placeholder="What needs to be done?">
    <el-button slot="prepend" icon="el-icon-arrow-down"></el-button>
  </el-input>
</template>
<script>
import Vue from "vue";
import { Input } from "element-ui";

Vue.use(Input);

export default {
  data() {
    return {
      input: ""
    };
  }
};
</script>
<style scoped>
.input {
  font-size: 18px;
}
</style>