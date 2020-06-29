<template>
  <div>
    <h1>Todos List</h1>
    <h3 v-if="loading">
      Loding...
    </h3>
    <Todo
      v-for="todo in todos"
      :id="todo.id"
      :key="todo.id"
      :title="todo.title"
      :completed="todo.completed"
    />
  </div>
</template>

<script>
import axios from 'axios'
import Todo from '../../components/Todo'
export default {
  components: {
    Todo
  },
  data () {
    return {
      todos: [],
      loading: false
    }
  },
  async created () {
    this.loading = true
    try {
      const res = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      this.todos = res.data
      this.loading = false
    } catch (error) {
      // console.log(error)
    }
    // console.log(res)
  }
}
</script>

<style scoped>
  div{
    margin: 2% 15%;
    width: fit-content;
  }
  h1{
    border-left: 15px solid rgb(40, 184, 112);
    border-bottom: 5px solid rgb(40, 184, 112);
    padding: 5px;
    width: fit-content;
  }
  h3{
    color: rgb(63, 5, 5);
  }
</style>
