<template>
  <div class="add-task">
    <input
      type="text"
      v-model="newItem"
      placeholder="Type and enter..."
      @keyup.enter="onAddItem"
    />
    <button class="add-btn" @click="onAddItem">+Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
    };
  },
  methods: {
    onAddItem() {
      this.$emit("add", this.newItem);
      this.newItem = "";
    },
  },
};
</script>

<style scoped>
.add-task {
  width: 100%;
  display: flex;
  justify-content: space-between;
}
.add-btn {
  height: 40px;
  font-size: 16px;
  font-weight: bolder;
  background-color: transparent;
  border: 0;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
  color: rgb(227, 250, 227);
  background-color: #a54cafce;
  box-shadow: 1px 1px 40px -10px #31505f30, 1px 1px 0px 0px #31505f30;
  padding: 0 10px;
}
.add-btn:hover {
  background-color: #51ed51;
}
.add-task input {
  width: 100%;
  height: 40px;
  border: 0;
  background-color: #f0f0f0d5;
  color: darkgray;
  font-size: 12px;
  font-weight: bold;
  border-radius: 8px 0 0 8px;
  padding: 0 0 0 15px;
  box-shadow: 1px 1px 40px -10px #31505f30, 0px 1px 2px 0px #31505f30;
  outline: none;
}
</style>
