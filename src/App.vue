<template>
  <div>
    <section class="todoapp">
      <Header v-on:addTodo='addTodo'/>
      <!-- This section should be hidden by default and shown when there are todos -->
      <Main :todos = "todos" v-on:deleteTodo='deleteTodo' v-on:handleBoxChange='handleBoxChange'/>
      <!-- This footer should hidden by default and shown when there are todos -->
      <Footer :todos='todos' v-on:handleActive='handleActive' v-on:all ='all' v-on:handleCompleted='handleCompleted'/>
    </section>
  </div>
</template>

<script>
import Main from "./components/Main"
import Header from "./components/Header"
import Footer from "./components/Footer"

export default {
  name: 'App',
  components: {
    Main,
    Header,
    Footer
  },
  data () {
    return {
      todos: [{id: '1', title: '吃饭', completed: true}, {id: '2', title: '睡觉', completed: false}]
    }
  },
  methods: {
    addTodo (item) {
      if (!item.trim()) {
        window.confirm('项目不能为空！')
        return
      }
      let todo = {id: Math.random(50), title: item, completed: false}
      this.todos.unshift(todo)
    },
    deleteTodo (id) {
      // 从任务数组中找到已经删除掉的任务的索引
      var index = this.todos.findIndex(item => item.id === id)
      // 将任务从数组中删除
      this.todos.splice(index, 1)
    },
    handleBoxChange (id) {
      // 将任务状态同步到任务数组中
      var task =  this.todos.find(item => item.id === id)
      console.log(task)
      // 更改任务状态
      task.completed = !task.completed
    },
    handleActive (active) {
      this.todos = active
    },
    all (all) {
      this.todos = all
    },
    handleCompleted (Completed) {
      this.todos = Completed
    }
  }
}
</script>

<style>

</style>
