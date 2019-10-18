<template>
  <el-checkbox-group v-model="completedTodos">
    <el-checkbox
      class="todo-item-wrapper"
      v-for="todo in todos"
      :label="todo"
      :key="todo"
      @change="handleComplete(todo)"
    >
      <span class="todo-item">{{todo}}</span>
      <el-link class="delete-btn" icon="el-icon-close" :underline="false" @click="deleteTodo(todo)"></el-link>
    </el-checkbox>
  </el-checkbox-group>
</template>
<script>
export default {
  data() {
    return {
      todos: [],
      completedTodos: [],
      checkedAll: false
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    handleComplete(todo) {
      this.completedTodos.push(todo);
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter(item => item !== todo);
    },
    toggleCheckAll() {
      this.checkedAll
        ? (this.completedTodos = [])
        : (this.completedTodos = this.todos);
      this.checkedAll = !this.checkedAll;
    }
  }
};
</script>
<style scoped>
.todo-item-wrapper {
  display: block;
  margin: 30px 20px !important;
  height: 30px;
  display: flex;
  border-bottom: solid 1px #dcdfe6;
  position: relative;
}

.todo-item {
  font-size: 20px;
  margin: 0 10px;
}

.todo-item-wrapper >>> .el-checkbox__inner::after {
  width: 4px;
  height: 8px;
  left: 6px;
  top: 3px;
}

.todo-item-wrapper >>> .el-checkbox__inner {
  width: 20px;
  height: 20px;
  border-radius: 50%;
}

.delete-btn {
  position: absolute;
  right: 10px;
}
</style>