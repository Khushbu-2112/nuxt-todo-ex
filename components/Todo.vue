<template>
  <nuxt-link :to="'todos/'+id">
    <div class="todo">
      <p :class="{'lth':completed}">
        {{ title }}
      </p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: 'Todo',
  props: {
    title: {
      type: String,
      default: ''
    },
    completed: Boolean,
    id: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style>
  .todo{
    padding: 1rem;
    margin: 1rem 0;
  }
  .lth{
    text-decoration: line-through;
  }
  a{
    text-decoration: none;
    color: rgb(18, 18, 46);
  }
</style>
