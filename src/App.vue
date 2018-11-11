<template>
  <div id="app">
    <img width="15%" src="./assets/logo.png">
    <h1>{{ title }}</h1>
    <TodoList/>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    TodoList
  },
  data() {
    return {
      title: "Welcome to Your Todo List!"
    };
  }
};
</script>

<style lang="scss">
@import "./variables.scss";
#app {
  font-family: "Source Sans Pro", "Helvetica Neue", Arial, sans-serif;
  font-size: 15px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $vue-main;
  margin-top: 30px;
}
h1,
h2 {
  font-weight: normal;
}
button {
  margin-right: 5px;
}
button:focus,
input:focus {
  outline: none;
}
</style>
