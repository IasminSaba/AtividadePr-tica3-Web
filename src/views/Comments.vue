<template>
  <div>
   <ul>
     <li v-for="comment in comments" :key="comment.id">
        <h1> PostId: {{comment.postId}} Id {{comment.id}} </h1>
        <p> Nome: {{comment.name}}  </p>
        <p> Email: {{comment.email }}  </p>
        <p> Body: {{comment.body}}  </p>
     </li>
   </ul>
   <button @click="fetchComments">Fetch Comments</button>
 </div>
</template>

<script>
export default {
    name: "Comments",
    data () {
        return {
          comments: [],
          baseURI: "https://jsonplaceholder.typicode.com/comments"
        };
    },
    methods: {
        fetchComments: function() {
            this.$http.get(this.baseURI).then((result) => {
            this.comments = result.data.filter(function(u){
                    return parseInt(u.id) % 2 == 0
                })
            });
        },
    },
}
</script>

<style>

</style>