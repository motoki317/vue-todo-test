<template>
  <div id="app">
    <counter />
    <timer />
    <item-list />
    <todo-list />
  </div>
</template>

<script>
import Counter from "./Counter.vue";
import Timer from "./Timer.vue";
import ItemList from "./ItemList.vue";
import TodoList from "./TodoList.vue";

export default {
  name: "app",
  props: {
    msg: String
  },
  components: {
    Counter,
    Timer,
    ItemList,
    TodoList
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
  margin-top: 60px;
}
</style>
