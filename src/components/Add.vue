<template>
  <div class="col-md-4">
    <form class="form-horizontal">
      <div class="form-group">
        <label>用户名</label>
        <input type="text" v-model="username" class="form-control" placeholder="用户名" />
      </div>
      <div class="form-group">
        <label>评论内容</label>
        <textarea
          class="form-control"
          rows="6"
          placeholder="评论内容"
          v-model="content"
        ></textarea>
      </div>
      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button type="button" class="btn btn-default pull-right" @click="handleClick">提交</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Add',
  data () {
    return {
      username: '',
      content: ''
    }
  },
  methods: {
    handleClick () {
      // 数据验证
      const username = this.username.trim()
      const content = this.content.trim()
      console.log(username, content)
      if (!username && !content) {
        alert('Please enter a username')
        return
      }
      const userData = {username, content}
      // 自定义事件
      this.$emit('add', userData)
      this.username = ''
      this.content = ''
    }
  }
}
</script>

<style scoped>
</style>
