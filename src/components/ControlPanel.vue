<template>
  <el-row class="control-panel">
    <el-col :span="6" class="items-left">{{leftItemsCount}} items left</el-col>
    <el-col :span="12">
      <el-menu :default-active="activeIndex" mode="horizontal" @select="handleSelect">
        <el-menu-item index="1">All</el-menu-item>
        <el-menu-item index="2">Active</el-menu-item>
        <el-menu-item index="3">Completed</el-menu-item>
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
      activeIndex: "1"
    };
  },
  methods: {
    handleSelect() {},
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