<template>
  <div class="main">
    <TaskList />
  </div>
</template>

<script>
import TaskList from "@/components/TaskList.vue";
export default {
  name: "App",
  components: { TaskList },
  data() {
    return {};
  },
};
</script>

<style>
#app {
  font-family: Segoe print;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #152f70;
  margin-top: 60px;
}
button,
input {
  font-family: Segoe print;
}
.main {
  font-family: Segoe print;
  width: 80%;
  background-color: rgba(38, 0, 255, 0.144);
  margin: auto;
  border: 1px solid rgb(226, 226, 226);
  box-shadow: 1px 1px 40px -10px #31505f30, 0px 1px 2px 0px #31505f30;
  border-radius: 20px 20px;
  padding: 20px;
}
</style>
