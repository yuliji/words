<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Words msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Words from './components/Words.vue'

export default {
  name: 'App',
  components: {
    Words
  }
}
</script>

