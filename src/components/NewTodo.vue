<template>
  <el-input class="input" v-model="input" placeholder="What needs to be done?">
    <el-button slot="prepend" icon="el-icon-arrow-down" @click="handleCheckAll"></el-button>
    <el-button slot="append" icon="el-icon-plus" @click="handleAddTodo"></el-button>
  </el-input>
</template>
<script>
export default {
  data() {
    return {
      input: ""
    };
  },
  methods: {
    handleCheckAll() {},
    handleAddTodo() {
      this.$emit("add-todo", this.input);
      this.input = "";
    }
  }
};
</script>
<style scoped>
.input {
  font-size: 18px;
}
</style>