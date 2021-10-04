<template>
  <div id="app" class="my-0">
      <my-header></my-header>
      <section-manager></section-manager>
  </div>
</template>

<script>
import SectionManager from './components/SectionManager.vue'
import MyHeader from './components/MyHeader.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    SectionManager
  },
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
