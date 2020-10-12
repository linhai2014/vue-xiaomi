<template>
  <div id="app">
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style lang="less">
  html,body,#app {
    height: 100%;
    width: 100%;
    padding: 0;
    margin: 0;
  }

</style>
