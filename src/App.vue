<template>
  <div id="app">
    <div class="container">
      <PostsList />
    </div>
  </div>
</template>

<script>
import PostsList from "./components/PostsList";
export default {
  name: "App",
  components: { PostsList },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
