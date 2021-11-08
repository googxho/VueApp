<template>
      <div class="col-md-8">
        <h3 class="reply">评论回复：</h3>
        <h2 v-show="list.length <= 0">暂无评论，点击左侧添加评论！！！</h2>
          <Item :list ="list" v-on:deleteItem ="deleteItem"/>
      </div>
</template>

<script>
import Item from './Item'

export default {
  name: 'List',
  props: {list: []},
  components: {
    Item
  },
  methods: {
    deleteItem (index) {
      console.log('list', index)
      this.$emit('deleteItem', index)
    }
  }
}
</script>

<style scoped>

</style>
