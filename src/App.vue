<template>
    <div>
      <header class="site-header jumbotron">
        <div class="container">
          <div class="row">
            <div class="col-xs-12">
              <h1>请发表对Vue的评论</h1>
            </div>
          </div>
        </div>
      </header>
      <div class="container">
        <Add v-on:add='add'/>
        <List :list='list' v-on:deleteItem='deleteItem'/>
      </div>
    </div>
</template>

<script>
import Add from './components/Add'
import List from './components/List'

export default {
  name: 'App',
  components: {
    Add,
    List
  },
  data () {
    return {
      list: [{username: 'Jeck', content: 'Vue不错！'}, {username: 'Tom', content: 'Vue Goog!'}]
    }
  },
  methods: {
    add (userDate) {
      console.log(userDate)
      this.list.unshift(userDate)
    },
    deleteItem (index) {
      console.log('app', index)
      this.list.splice(index, 1)
    }
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
