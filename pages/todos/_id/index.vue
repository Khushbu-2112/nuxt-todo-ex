<template>
  <div>
    <nuxt-link to="/todos">
      Go Back
    </nuxt-link>
    <br>
    <h2>Title: {{ todo.title }}</h2>
    <small>Todo Id: {{ $route.params.id }}</small>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      todo: {}
    }
  },
  async created () {
    try {
      const res = await axios.get(`https://jsonplaceholder.typicode.com/todos/${this.$route.params.id}`)
      this.todo = res.data
      // console.log(this.todo)
    } catch (error) {
      // console.log(error)
    }
  }
}
</script>

<style scoped>
  div{
    margin: 2% 15%;
  }
  h2{
    margin: 2%;
    color: rgb(0, 128, 79);
  }
</style>
