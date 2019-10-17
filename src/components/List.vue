<template>
  <el-checkbox-group v-model="checkedTodos" @change="handleCheckedTodosChange">
    <el-checkbox class="todo-item" v-for="todo in todos" :label="todo" :key="todo">{{todo}}</el-checkbox>
  </el-checkbox-group>
</template>
<script>
export default {
  props: { todos: Array },
  data() {
    return {
      checkAll: false,
      checkedTodos: []
    };
  },
  methods: {
    handleCheckedTodosChange(value) {
      let checkedCount = value.length;
      this.checkAll = checkedCount === this.todos.length;
    }
  }
};
</script>
<style scoped>
.todo-item {
  display: block;
  margin: 20px 10px;
  text-align: left;
}
</style>