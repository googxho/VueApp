<template>
  <div>
    <header class="header">
      <h1>todos</h1>
      <input
        type="text"
        class="new-todo"
        placeholder="What needs to be done?"
        autofocus
        id="task"
        v-model="todoItem"
        @keyup.enter="onSubmit"
      />
    </header>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      todoItem: ''
    }
  },
  methods: {
    onSubmit () {
      this.$emit('addTodo', this.todoItem)
      this.todoItem = ''
    }
  }
}
</script>

<style scoped>

</style>
