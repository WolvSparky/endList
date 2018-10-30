<template>
  <div id="app">
    <PostsList />
  </div>
</template>

<script>
import PostsList from './components/PostsList.vue';

export default {
  name: 'app',
  components: {
    PostsList,
  },
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
