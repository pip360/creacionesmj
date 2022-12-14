<template>
<center>
  <div>
    <h3>Registro Productos</h3>
    <div class="card" style="width: 35rem">
      <div class="card-body">
        <h4 class="card-title">Datos Producto</h4>

        
        <div class="form-group">
          <label for="formGroupExampleInput">Codigo</label>
          <input
            v-model="codigo"
            type="text"
            class="form-control"
            placeholder="#"
          />
        </div>
        <div class="form-group">
          <label for="formGroupExampleInput">Nombre</label>
          <input
            v-model="nombre"
            type="text"
            class="form-control"
            placeholder="Multiusos/Pijama"
          />
        </div>
        <div class="form-group">
        </div>
        <div class="form-group">
          <label for="formGroupExampleInput2">Precio</label>
          <input
            v-model="precio"
            type="text"
            class="form-control"
            placeholder="$"
          />
        </div>
        <button class="btn btn-primary" @click="addPersona">
          Agregar
        </button>
      </div>
    </div>
  </div>
  </center>
   <br><br>
     
</template>


<script>
/*eslint-disable*/
import {ref} from 'vue'
import {useStore} from 'vuex'
import {useRouter} from 'vue-router'
import axios from 'axios'
export default {
  setup(){
    const store = useStore()
    const router = useRouter()
    const nombre = ref("")
    const codigo = ref("")
    const precio = ref("")
    
    function addPersona(){
      if(nombre.value != '' && codigo.value != "" && precio.value != ""){
        const persona = {
          nombre:nombre.value,
          codigo:codigo.value,
          precio:precio.value
        }
        axios.post('https://creaciones-maria-jose-default-rtdb.firebaseio.com/producto.json',persona)
        .then(res => console.log(res))
        .catch(error => console.log(error))
      }
    }

    return{nombre,codigo, precio, addPersona}
  }
};
</script>