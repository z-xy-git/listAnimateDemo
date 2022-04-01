<template>
  <div id="app">
    <List-Ani></List-Ani>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
import ListAni from './components/ListAni.vue'

export default {
  name: 'App',
  components: {
    ListAni
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
