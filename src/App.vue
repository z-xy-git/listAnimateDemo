<template>
  <div id="app">
    <!-- <List-Ani></List-Ani> -->
    <list-animate></list-animate>
  </div>
</template>

<script>
// import ListAni from './components/ListAni.vue';
import listAnimate from './components/ListAnimate.vue';

export default {
  name: 'App',
  components: {
    // ListAni,
    listAnimate
  }
}
</script>

<style>
#app {
  color: #2c3e50;
  margin-top: 60px;
  margin-left: 200px;
}
</style>
