/* eslint-disable */

<template>
  <div>
    <div v-for="(item, index) in todos" :key="index">
      <li :class="item.completed ? 'completed' : ''">
        <div class="view">
          <input class="toggle" type="checkbox" :checked="item.completed" @change="handleBoxChange(item.id)" />
          <label>{{item.title}}</label>
          <button class="destroy" @click="deleteTodo(item.id)"></button>
        </div>
        <input class="edit" />
      </li>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Item',
  props: { todos: [] },
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
