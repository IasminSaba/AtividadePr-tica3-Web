<template>
 <div>
   <ul>
     <li v-for="user in users" :key="user.id">
       
       <h4>{{user.id }} {{ user.name }}</h4>
       <p> Username: {{user.username}} </p> 
       <p> Email: {{ user.email }}</p>
       <p> Endereço: {{user.address.street}}, {{user.address.suite}} - {{user.address.city}} - {{user.address.zipcode}} </p>  
       <p> Geocalização: {{user.address.geo.lat}} {{user.address.geo.lng}} </p> 
       <p> Telefone: {{user.phone}} </p>      
       <p> Website: {{user.website}} </p>
       <p> Companhia: {{user.company.name}} - {{user.company.catchPhrase}} - {{user.company.bs}} </p>

     </li>
   </ul>
   <button @click="fetchUsers">Fetch Users</button>
 </div>
</template>


<script>
export default {
 name: "Users",
 data() {
   return {
     users: [],
     baseURI: "https://jsonplaceholder.typicode.com/users"
   };
 },
 methods: {
   fetchUsers: function() {
     this.$http.get(this.baseURI).then((result) => {
       this.users = result.data;
       this.users = this.users.slice(0,6);
     });
   },
 },
};

</script>

<style>

</style>