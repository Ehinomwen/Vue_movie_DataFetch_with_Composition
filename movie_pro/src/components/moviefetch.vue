<template>
  
  <main>
    <h1>Lastest Movies</h1>
    <div class="inputbut">
      <input v-model="search" type="search" name="" id="">
      <button @click="getPosts">search</button>
    </div>
    <div >
   <ul>
    <li v-for="post in post">{{ post }}</li>
   </ul>
    </div>
    
  </main>

</template>

<script setup>
import { ref } from 'vue'

const search = ref('')
const post = ref([])

const getPosts =() =>{
  if(search.value !='')
  fetch(`http://www.omdbapi.com/?i=tt3896198&apikey=4fc450c6`)
      .then(response => response.json())
      .then(data => post.value = data)

      
      return{
  post,
  search
}

} 
</script>

<style scoped>
main{
  display: flex;
  
  justify-content: center;
  
}
.inputbut{
  position: absolute;
  margin-top: 100px;
  margin-right: 50px;
   /* background-color: blue; */
}
button{
  
  position: absolute;
  border-left: none;
  margin-right: 50px;
  background-color: whitesmoke;
  border: 2px solid  rgba(16, 5, 5, 0.287);
  height: 30px;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
}
input{
  width: 255px;
  border-right: none;
  background-color: whitesmoke;
  border: 2px solid rgba(16, 5, 5, 0.287);
  height: 30px;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
}
ul{
  background-color: chocolate;
  color: rgb(231, 222, 240);
  margin-top: 100px;
  font-size: 15px;
  border-radius: 20px;
}
h1{
  font-size: 30px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 600;
  color: blue;
}

</style>