<template>
  <div class="container">
    <Search />
    <UserMain />
  </div>
</template>

<script>
import Search from './components/Search.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  data () {
    return {
      // input: 'eee'
    }
  },
  components: {
    Search, UserMain: Main
  },
  mothods: {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
