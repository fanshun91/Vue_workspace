<template>
  <div id="app">
    <input type="text" v-model="inputVal">
    <button @click="handleSubmit">提交</button>
    <ul>
      <todo-item 
        v-for="(item, index) of list"
        :key="index"
        :content="item"
        :index="index"
        @delete="handleDelete"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem";

export default {
  name: "app",
  components: {
    TodoItem
  },
  data() {
    return {
      inputVal: "",
      list: []
    };
  },
  methods: {
    handleSubmit() {
      this.list.push(this.inputVal);
      this.inputVal = "";
    },
    handleDelete(index) {
      this.list.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
