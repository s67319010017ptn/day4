<template>
  <div id="app">
    <h1>รายการโพสต์จาก API</h1>
    <PostList />
  </div>
</template>

<script>
import PostList from './components/PostList.vue';

export default {
  name: 'App',
  components: {
    PostList,
  },
};
</script>

<style>
#app {
  text-align: center;
  padding: 20px;
  background-color: #f9f9f9;
  min-height: 100vh;
  color: #333;
}
h1 {
  margin-bottom: 20px;
}
</style>
