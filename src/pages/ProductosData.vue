<template>
  <div>
    <h3>Lista de productos</h3>

    <ul class="list-group">
      <li v-for="(personas, i) in personas" :key="i"  class="list-group-item">
        <router-link :to="`/details/${personas.id}`">{{
          personas.nombre
        }}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
import {ref} from 'vue'
export default {
  setup(){
    const personas = ref([])
    axios.get('https://creaciones-maria-jose-default-rtdb.firebaseio.com/producto.json',personas)
    .then(res=>{
      console.log(res)
      for(const id in res.data){
        personas.value.push({
          id:id,
          nombre: res.data[id].nombre,
          codigo: res.data[id].codigo,
          /* mail: res.data[id].email, */
          precio: res.data[id].precio,
        })
      }
    })
   .catch(error => console.log(error))
   return {personas};
  }
  /* computed: {
    personas() {
      return this.$store.getters.getPersonas;
    },
  }, */
};
</script>

<style>
div{
color-scheme: black;
}
</style>