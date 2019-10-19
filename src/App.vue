<template>
  <div id="app">
    <h1>todos</h1>
    <new-todo @add-todo="addTodo" @toggle-check-all="toggleCheckAll"></new-todo>
    <todo-list ref="todoList"></todo-list>
  </div>
</template>

<script>
import NewTodo from "./components/NewTodo.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
  components: {
    NewTodo,
    TodoList
  },
  methods: {
    addTodo(todo) {
      this.$refs.todoList.addTodo(todo);
    },
    toggleCheckAll() {
      this.$refs.todoList.toggleCheckAll();
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 500px;
}
</style>
