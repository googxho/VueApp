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
import PubSub from 'pubsub-js'

export default {
  name: 'Item',
  props: { todos: [] },
  methods: {
    deleteTodo (id) {
      // 发布消息
      PubSub.publish('deleteTodo', id)
      // 老办法
      // console.log(id)
      // this.$emit('deleteTodo', id)
    },
    handleBoxChange (id) {
      this.$emit('handleBoxChange', id)
    }
  }
}
</script>

<style scoped>
</style>
