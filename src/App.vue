<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <PostsList msg="list" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import PostsList from "./components/PostsList.vue";

export default {
  name: "app",
  components: {
    HelloWorld,
    PostsList
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
