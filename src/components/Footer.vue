<template>
      <footer class="footer">
        <!-- This should be `0 items left` by default -->
        <span class="todo-count"><strong id="count">{{count}}</strong> item left</span>
        <!-- Remove this if you don't implement routing -->
        <ul class="filters">
          <li>
            <a class="selected" href="javascript:;" @click="all">All</a>
          </li>
          <li>
            <a href="javascript:;" @click="handleActive">Active</a>
          </li>
          <li>
            <a href="javascript:;" @click="handleCompleted">Completed</a>
          </li>
        </ul>
        <!-- Hidden if no completed items are left ↓ -->
        <button class="clear-completed" id="clear" >Clear completed</button>
      </footer>
</template>

<script>
import Item from './Item'
import storageTodo from '../util/todoStorage'
export default {
  name: 'List',
  data () {
    return {
    }
  },
  props: { todos: [] },
  components: {
    Item
  },
  computed: {
    count () {
      return this.todos.length
    }
  },
  methods: {
    deleteItem (index) {
      console.log('list', index)
      this.$emit('deleteItem', index)
    },
    all (index) {
      const all = storageTodo.readTodo()
      console.log('all', all)
      this.$emit('all', all)
    },
    handleActive () {
      const active = storageTodo.readTodo().filter(item => item.completed === false)
      this.$emit('handleActive', active)
    },
    handleCompleted () {
      const completed = storageTodo.readTodo().filter(item => item.completed === true)
      this.$emit('handleCompleted', completed)
    }
  }
}
</script>

<style scoped>

</style>
