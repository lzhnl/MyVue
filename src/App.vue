<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <animation></animation>
    <graph></graph>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import graph from "@/components/graph";
import animation from "@/components/animation";
export default {
  name: 'App',
  components: {
    HelloWorld,
    graph,
    animation
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
