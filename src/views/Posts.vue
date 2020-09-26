<template>
  <div>
   <ul>
     <li v-for="post in posts" :key="post.id">
        <h1> UserId: {{post.userId}} Id {{post.id}} </h1>
        <p> Título: {{post.title}}  </p>
        <p> Body: {{post.body}}  </p>
     </li>
   </ul>
   <button @click="fetchPosts">Fetch Posts</button>
 </div>
</template>

<script>
export default {
    name: "Posts",
    data () {
        return {
          posts: [],
          baseURI: "https://jsonplaceholder.typicode.com/posts"
        };
    },
    methods: {
        fetchPosts: function() {
            this.$http.get(this.baseURI).then((result) => {
            this.posts = result.data.filter(function(u){
                    return parseInt(u.id) % 2 == 1
                })
            });
        },
    },
}
</script>

<style>

</style>