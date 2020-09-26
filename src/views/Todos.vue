<template>
  <div>
   <ul>
     <li v-for="index in todos" :key="index.id">
       <h4> UserId: {{index.userId }} id: {{ index.id }} </h4>
       <p> Title: {{index.title}} </p>
       <p> Status completed: {{index.completed}} </p>
     </li>
   </ul>
   <button @click="fetchTodos">Fetch Todos</button>
 </div>
</template>

<script>
export default {
    name: "Todos",
    data () {
        return {
            todos: [],
            baseURI: "https://jsonplaceholder.typicode.com/todos"
        };
    },
    methods: {
        fetchTodos: function() {
            this.$http.get(this.baseURI).then((result) => {
                this.todos = result.data;
                this.todos = this.todos.filter(function(u){
                    return (u.userId == 2) && (u.completed)
                })
            });
        },
    },
}
</script>

<style>

</style>