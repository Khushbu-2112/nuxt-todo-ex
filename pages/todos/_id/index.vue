<template>
  <div>
    <nuxt-link to="/todos">
      <label class="button--green">Go Back</label>
    </nuxt-link>
    <br>
    <br>
    <div class="box">
      <h2>Title: {{ todo.title }}</h2>
      <small>Todo Id: {{ $route.params.id }}</small>
      <br>
      <br>
      <button v-if="!todo.completed" class="button--green" @click="completeTodo">
        Complete
      </button>
      <button class="button--grey" @click="delTodo">
        Delete
      </button>
    </div>
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
  },
  methods: {
    async delTodo () {
      await axios.delete(`https://jsonplaceholder.typicode.com/todos/${this.$route.params.id}`)
        .then(() => {
          this.$router.push({ path: '/todos' })
        })
        .catch((e) => {
          // console.log(e)
        })
        // console.log(this.todo)
    },
    async completeTodo () {
      await axios.patch(`https://jsonplaceholder.typicode.com/todos/${this.$route.params.id}`, { completed: true })
        .then(() => {
          this.$router.push({ path: '/todos' })
        })
        .catch((e) => {
          // console.log(e)
        })
        // console.log(this.todo)
    }
  }
}
</script>

<style scoped>
  div{
    margin: 2% 15%;
  }
  h2{
    margin-bottom: 1%;
  }
  .box{
    border: 1px solid #35495e;
    border-radius: 5px;
    box-shadow: 0px 2px 2px #ccc;
    width: fit-content;
    padding: 15px;
    margin: 0 auto;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    text-align: center;
  }
  small{
    color: #35495e;
  }
</style>
