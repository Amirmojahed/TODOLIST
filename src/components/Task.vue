<template>
  <div class="task">
    <ul>
      <li @click="onCheckingTask(item)" :class="{ checked: item.check }">
        {{ item.name }}
      </li>
      <button class="remove-btn" @click="onRemoveTask(index)">×</button>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
    },
    index: {
      type: Number,
    },
  },
  methods: {
    onRemoveTask(index) {
      console.log("iindex", index);
      this.$emit("remove", index);
    },
    onCheckingTask(item) {
      this.$emit("check", item);
    },
  },
};
</script>

<style scoped>
h1 {
  color: rgba(56, 53, 206, 0.685);
  background-color: transparent;
  box-shadow: 1px 1px 40px -10px #31505f30, 1px 1px 0px 0px #31505f30;
  text-shadow: 1px 1px #31505f30;
  padding: 10px;
  border-radius: 10px;
}
h1:hover {
  color: transparent;
}
.task {
  width: 90%;
  font-size: 12px;
  text-shadow: 1px 1px #31505f30;
  font-weight: bold;
  margin: auto;
}
ul {
  padding: 5px;
  position: relative;
}
ul li {
  cursor: pointer;
  list-style: none;
  border-bottom: 1px solid rgb(192, 190, 211);
  display: flex;
  font-size: 16px;
  padding-bottom: 20px;
  color: #152f70;
}
ul li:hover {
  color: #dd51ed;
}
ul li.checked {
  text-decoration: line-through;
  color: #dd51ed;
}
.remove-btn {
  font-size: 20px;
  background-color: transparent;
  border: 0;
  padding: 0;
  cursor: pointer;
  position: absolute;
  top: 0;
  right: 0;
  color: #152f70;
}
.remove-btn:hover {
  color: #dd51ed;
}
</style>
