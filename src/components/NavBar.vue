<template>
  <div class="nav-bar">
    <button
      @click="onChangeFilter('viewAll')"
      :class="{ active: filter === 'viewAll' }"
    >
      All
    </button>
    <button
      @click="onChangeFilter('viewCompleted')"
      :class="{ active: filter === 'viewCompleted' }"
    >
      Completed
    </button>
    <button
      @click="onChangeFilter('viewUncompleted')"
      :class="{ active: filter === 'viewUncompleted' }"
    >
      Uncompleted
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filter: "viewAll",
    };
  },
  methods: {
    onChangeFilter(filter) {
      this.filter = filter;
      this.$emit("filter", filter);
    },
  },
};
</script>

<style scoped>
.nav-bar {
  display: flex;
  justify-content: space-around;
  padding: 5px;
}
button {
  min-width: 30%;
  margin: auto;
  height: 40px;
  margin: 3px;
  font-size: 11px;
  font-weight: bold;
  border: 0;
  border-radius: 8px;
  color: #152f70;
  cursor: pointer;
  background-color: transparent;
  box-shadow: 1px 1px 20px -2px #31505f30, 0px 1px 2px 0px #31505f30;
}
button:hover {
  background-color: #5451edbd;
}
button.active {
  background-color: #5451edbd;
}
</style>
