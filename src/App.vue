<template>
  <div id="app">
    <h1>todos</h1>
    <new-todo></new-todo>
    <List></List>
  </div>
</template>

<script>
import NewTodo from "./components/NewTodo.vue";
import List from "./components/List.vue";

export default {
  name: "app",
  components: {
    NewTodo,
    List
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
