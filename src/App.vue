<template>
  <signupformVue />
</template>

<script>

import signupformVue from './components/signupform.vue';
export default {
  name: 'App',
  components: {
    signupformVue
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  margin: 0;
  background: #eee;
}
</style>
