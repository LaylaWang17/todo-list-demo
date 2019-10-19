<template>
  <el-row class="control-panel">
    <el-col :span="6" class="items-left">{{leftItemsCount}} items left</el-col>
    <el-col :span="12">
      <el-menu :default-active="activeIndex" mode="horizontal" @select="handleSelect">
        <el-menu-item index="all">All</el-menu-item>
        <el-menu-item index="active">Active</el-menu-item>
        <el-menu-item index="completed">Completed</el-menu-item>
      </el-menu>
    </el-col>
    <el-col :span="6" class="button-wrapper">
      <el-button @click="clearCompleted">Clear completed</el-button>
    </el-col>
  </el-row>
</template>
<script>
export default {
  props: ["left-items-count"],
  data() {
    return {
      activeIndex: "all"
    };
  },
  methods: {
    handleSelect(key) {
      this.$emit("toggle-display-mode", key);
    },
    clearCompleted() {
      this.$emit("clear-completed");
    }
  }
};
</script>
<style scoped>
.control-panel {
  display: flex;
  align-items: flex-end;
}

.items-left {
  font-size: 14px;
  text-align: left;
}

.el-menu.el-menu--horizontal {
  border: none;
}

.el-menu--horizontal > .el-menu-item {
  height: 40px;
}

.button-wrapper {
  text-align: right;
}

.el-button {
  font-size: 14px;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  font-weight: normal;
  border: none;
  padding: 0;
}

.el-button:hover {
  background: #ffffff;
}
</style>