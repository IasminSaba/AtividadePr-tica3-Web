<template>
  <div>
   <ul>
     <li v-for="photo in photos" :key="photo.id">
       <img v-bind:src=photo.url v-bind:alt="alt">
     </li>
   </ul>
   <button @click="fetchPhotos">Fetch Photos</button>
 </div>
</template>

<script>
export default {
    name: "Photos",
    data () {
        return{
            photos: [],
            baseURI: "https://jsonplaceholder.typicode.com/photos",
            img: String,
            alt: "alt"
        };
    },
    methods: {
        fetchPhotos: function() {
            this.$http.get(this.baseURI).then((result) => {
            this.photos = result.data.filter(function(u){
                    return u.albumId == 3
                })
            });
        },
    },
        
}
</script>

<style>

</style>