<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
    <Users> </Users>
    <Todos> </Todos>
    <Photos> </Photos>
    <Comments> </Comments>
    <Posts> </Posts>
  </div>
</template>

<script>
import Users from './views/Users.vue'
import Todos from './views/Todos.vue'
import Photos from './views/Photos.vue'
import Comments from './views/Comments.vue'
import Posts from './views/Posts.vue'

export default {
  name: "App",
  components: {
    Users,
    Todos,
    Photos,
    Comments,
    Posts
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
