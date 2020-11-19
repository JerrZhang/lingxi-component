<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <count-down></count-down>
    <float-tips></float-tips>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import CountDown from './components/CountDown';
import FloatTips from './components/FloatTips';



export default {
  name: 'App',
  components: {
    HelloWorld,
    CountDown,
    FloatTips
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
</style>
