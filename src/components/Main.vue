<template>
  <div>
    <section class="main">
      <input class="toggle-all" type="checkbox" />
      <ul class="todo-list" id="todo-list">
        <Item :todos='todos' v-on:deleteTodo='deleteTodo' v-on:handleBoxChange='handleBoxChange'/>
      </ul>
    </section>
  </div>
</template>

<script>
import Item from './Item.vue'

export default {
  name: 'Main',
  props: {todos: []},
  components: { Item },
  data () {
    return {}
  },
  methods: {
    deleteTodo (id) {
      console.log(id)
      this.$emit('deleteTodo', id)
    },
    handleBoxChange (id) {
      this.$emit('handleBoxChange', id)
    }
  }
}
</script>

<style scoped>
</style>
