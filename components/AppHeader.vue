<template>
  <div>
    <!-- <img src="" alt="Logo"> -->
    <header class="head">
      <ul>
        <li>
          <nuxt-link to="/todos">
            Todos
          </nuxt-link>
        </li>
        <li>
          <nuxt-link to="/about">
            About
          </nuxt-link>
        </li>
      </ul>
    </header>
  </div>
</template>

<script>
export default {
  name: 'AppHeader'
}
</script>

<style scoped>

div{
  display: flex;
  justify-content: space-between;
}

.head{
  width: 100%;
   color: white;
   background:#35495e;
   font-size: 2rem;
}

ul{
  list-style: none;
  display: flex;
}

li{
  padding: 10px;
}

a{
  text-decoration: none;
  color: inherit;
}

.nuxt-link-active{
  color: rgb(40, 184, 112);
  -webkit-text-stroke-width: 0.2px;
  -webkit-text-stroke-color: white;
}

</style>
