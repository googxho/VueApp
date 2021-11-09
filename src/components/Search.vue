<template>
  <section class="jumbotron">
    <h3 class="jumbotron-heading">搜索GitHub用户</h3>
    <div>
      <input type="text" placeholder="GitHub用户名" v-model="searchInfo" />
      <button @click="searchUser">搜索</button>
    </div>
  </section>
</template>

<script>
import PubSub from 'pubsub-js'

export default {
  name: "Main",
  data () {
    return {
      searchInfo: "sss"
    }
  },
  methods: {
    searchUser () {
      const searchInfo = this.searchInfo.trim()
      if (searchInfo) {
        // 分发一个search的消息
        PubSub.publish("search", searchInfo)
      }
    }
  }
}
</script>

<style scoped>
</style>
