<template>
  <div>
    <el-checkbox
      class="todo-item-wrapper"
      v-for="todo in displayedTodos"
      :key="todo.id"
      :checked="todo.completed"
      @change="handleCheck(todo)"
    >
      <span class="todo-item">{{todo.title}}</span>
      <el-link class="delete-btn" icon="el-icon-close" :underline="false" @click="deleteTodo(todo)"></el-link>
    </el-checkbox>
  </div>
</template>
<script>
import uuid from "uuid/v1";

export default {
  data() {
    return {
      todos: [],
      displayedTodos: [],
      checkedAll: false,
      displayMode: "all"
    };
  },
  computed: {
    activeTodos: function() {
      return this.todos.filter(todo => !todo.completed);
    },
    completedTodos: function() {
      return this.todos.filter(todo => todo.completed);
    }
  },
  created() {
    if (!localStorage.getItem("todos")) {
      this.updateLocalStorage();
    }
    this.todos = JSON.parse(localStorage.getItem("todos"));
    this.checkedAll = this.todos.findIndex(item => !item.completed) === -1;
    this.showTodos(this.displayMode);
    this.$emit("count-left-items", this.countLeftItems());
  },
  updated() {
    this.$nextTick(function() {
      this.showTodos(this.displayMode);
      this.updateLocalStorage();
      this.$emit("count-left-items", this.countLeftItems());
    });
  },
  methods: {
    addTodo(todo) {
      this.todos.push({
        id: uuid(),
        title: todo,
        completed: false
      });
      this.showTodos(this.displayMode);
    },
    handleCheck(todo) {
      todo.completed = !todo.completed;
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter(item => item.id !== todo.id);
    },
    toggleCheckAll() {
      // if (this.checkedAll) {
      //   this.todos.forEach(todo => {
      //     todo.completed = false;
      //   });
      // } else {
      //   this.todos.forEach(todo => {
      //     todo.completed = true;
      //   });
      // }
      // this.checkedAll = !this.checkedAll;
      // this.updateLocalStorage();
    },
    countLeftItems() {
      return this.todos.filter(todo => !todo.completed).length;
    },
    clearCompleted() {
      this.todos = this.todos.filter(todo => !todo.completed);
      this.updateLocalStorage();
      this.showTodos(this.displayMode);
    },
    updateLocalStorage() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    showTodos(mode) {
      this.displayMode = mode;
      switch (mode) {
        case "active":
          this.displayedTodos = this.activeTodos;
          break;
        case "completed":
          this.displayedTodos = this.completedTodos;
          break;
        default:
          this.displayedTodos = this.todos;
          break;
      }
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
  border: 1px solid #409eff;
  border-left: 0;
  border-top: 0;
}

.todo-item-wrapper >>> .el-checkbox__inner {
  width: 20px;
  height: 20px;
  border-radius: 50%;
}

.todo-item-wrapper >>> .el-checkbox__input.is-checked .el-checkbox__inner {
  background: #ffffff;
}

.todo-item-wrapper >>> .el-checkbox__input.is-checked + .el-checkbox__label {
  color: #d9d9d9;
  text-decoration: line-through;
}

.delete-btn {
  position: absolute;
  right: 10px;
}
</style>