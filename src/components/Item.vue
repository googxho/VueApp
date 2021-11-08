
<template>
  <div>
    <ul class="list-group" v-for="(item, index) in List" :key="index">
      <li class="list-group-item">
        <div class="handle">
          <a href="javascript:;" @click="deleteItem(index)">删除</a>
        </div>
        <p class="user">
          <span>{{ item.username }}</span
          ><span>说:</span>
        </p>
        <p class="centence">{{ item.content }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Item',
  props: {
    List: []
  },
  methods: {
    deleteItem (index) {
      // 自定义删除事件
      console.log(index)
      this.$emit('deleteItem', index)
    }
  }
}
</script>

<style scoped>
</style>
