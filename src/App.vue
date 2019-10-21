<template>
  <div id="app">
    <h1>todos</h1>
    <new-todo @add-todo="addTodo" @toggle-check-all="toggleCheckAll"></new-todo>
    <todo-list
      ref="todoList"
      @count-left-items="countLeftItems"
      @toggle-clear-btn-visibility="toggleClearBtnVisibility"
    ></todo-list>
    <control-panel
      :left-items-count="leftItemsCount"
      :hide-clear-btn="hideClearBtn"
      @clear-completed="clearCompleted"
      @change-display-mode="changeDisplayMode"
    ></control-panel>
  </div>
</template>

<script>
import NewTodo from "./components/NewTodo.vue";
import TodoList from "./components/TodoList.vue";
import ControlPanel from "./components/ControlPanel";

export default {
  name: "app",
  components: {
    NewTodo,
    TodoList,
    ControlPanel
  },
  data() {
    return {
      leftItemsCount: 0,
      hideClearBtn: true
    };
  },
  methods: {
    addTodo(todo) {
      this.$refs.todoList.addTodo(todo);
    },
    toggleCheckAll() {
      this.$refs.todoList.toggleCheckAll();
    },
    countLeftItems(count) {
      this.leftItemsCount = count;
    },
    clearCompleted() {
      this.$refs.todoList.clearCompleted();
    },
    changeDisplayMode(mode) {
      this.$refs.todoList.changeDisplayMode(mode);
    },
    toggleClearBtnVisibility(visible) {
      this.hideClearBtn = visible;
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
  width: 550px;
}
</style>
