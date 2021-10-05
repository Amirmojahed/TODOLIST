<template>
  <div class="container">
    <h1 class="title">To Do List</h1>
    <AddTask @add="onAddItem" />

    <div class="statusBar">
      <button class="checked-item__btn" @click="items.filter(completeAll)">
        Complete all
      </button>
      <button class="unchecked-item__btn" @click="items.filter(clearCompleted)">
        Clear Completed
      </button>
    </div>

    <Task
      v-for="(item, index) in items"
      :key="index"
      :item="item"
      :index="index"
      @remove="onRemoveTask"
      @check="onCheckingTask"
    />
    <NavBar @filter="onChangeFilter" />
  </div>
</template>

<script>
import AddTask from "@/components/AddTask.vue";
import NavBar from "./NavBar.vue";
import Task from "@/components/Task.vue";
export default {
  components: { AddTask, Task, NavBar },
  data() {
    return {
      filter: "viewAll",
      items: [
        { name: "Clean", status: true, check: false },
        { name: "Bye Bitcoin", status: true, check: false },
        { name: "Bye Doge", status: true, check: false },
      ],
    };
  },
  watch: {
    filter(val) {
      switch (val) {
        case "viewAll":
          return this.items.filter((item) => (item.status = true));

        case "viewCompleted":
          return this.items.filter((item) =>
            item.check ? (item.status = true) : (item.status = false)
          );

        case "viewUncompleted":
          return this.items.filter((item) =>
            !item.check ? (item.status = true) : (item.status = false)
          );
      }
    },
  },

  methods: {
    onAddItem(newItem) {
      if (newItem === "") {
        alert("You must write something!");
      } else {
        this.items.push({
          name: newItem,
          status: true,
          check: false,
        });
      }
    },
    onRemoveTask(index) {
      this.items.splice(index, 1);
    },
    onCheckingTask(item) {
      item.check = !item.check;
    },
    completeAll(array) {
      if (!array.check) array.check = true;
    },
    clearCompleted(array) {
      if (array.check) {
        array.check = false;
      }
    },
    onChangeFilter(filter) {
      this.filter = filter;
    },
  },
};
</script>

<style scoped>
.container {
  width: 90%;
  margin: auto;
  color: #303030;
}

h1.title {
  color: rgba(56, 53, 206, 0.685);
  background-color: transparent;
  box-shadow: 1px 1px 40px -10px #31505f30, 1px 1px 0px 0px #31505f30;
  text-shadow: 1px 1px #31505f30;
  padding: 10px;
  border-radius: 10px;
  user-select: none;
}
h1.title:hover {
  color: transparent;
}
.statusBar {
  display: flex;
  padding: 20px 0;
}
.checked-item__btn {
  min-width: 50%;
  margin: auto;
  height: 40px;
  margin: 3px;
  font-size: 11px;
  font-weight: bold;
  border: 0;
  border-radius: 8px;
  color: #152f70;
  cursor: pointer;
  background-color: #5451edbd;
  box-shadow: 1px 1px 20px -5px #31505f30, 0px 1px 2px 0px #31505f30;
}
.checked-item__btn:hover {
  background-color: #96d686d8;
}
.unchecked-item__btn {
  min-width: 50%;
  margin: auto;
  height: 40px;
  margin: 3px;
  font-size: 11px;
  font-weight: bold;
  border: 0;
  border-radius: 8px;
  color: #152f70;
  cursor: pointer;
  background-color: #5451edbd;
  box-shadow: 1px 1px 20px -5px #31505f30, 0px 1px 2px 0px #31505f30;
}
.unchecked-item__btn:hover {
  background-color: #ec6c6cbd;
}
</style>
