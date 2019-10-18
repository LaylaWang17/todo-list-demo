<template>
  <el-checkbox-group v-model="completedTodos">
    <el-checkbox
      class="todo-item"
      v-for="todo in todos"
      :label="todo"
      :key="todo"
      @change="handleComplete(todo)"
    >
      <span>{{todo}}</span>
      <el-link icon="el-icon-close" :underline="false" @click="deleteTodo(todo)"></el-link>
    </el-checkbox>
  </el-checkbox-group>
</template>
<script>
export default {
  data() {
    return {
      todos: [],
      completedTodos: []
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