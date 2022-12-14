<template>
<center>
    <div>
      <h3>Registro Usuarios</h3>
      <div class="card" style="width: 35rem">
        <div class="card-body">
          
  
          <div class="form-group">
            <h5 class="card-title">Datos Personal</h5>
            <label for="formGroupExampleInput">Correo</label>
            <input
              v-model="nombreusuario"
              type="text"
              class="form-control"
              placeholder="hola@gmail.com"
            />
          </div>
          <div class="form-group">
            <label for="formGroupExampleInput2">Contraseña</label>
            <input
              v-model="contra"
              type="text"
              class="form-control"
              placeholder="**********"
            />
          </div>
          <button class="btn btn-primary" @click="addPersonal">
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
      const nombreusuario = ref("")
      const contra = ref("")
      
      function addPersonal(){
        if(nombreusuario.value != '' && contra.value != ""){
          const personal = {
            nombreusuario:nombreusuario.value,
            contra:contra.value
          }
          /* store.dispatch("addPersona", persona);
          router.push('/print') */
          axios.post('https://creaciones-maria-jose-default-rtdb.firebaseio.com/persona.json',personal)
          .then(res => console.log(res))
          .catch(error => console.log(error))
        }
      }
  
      return{nombreusuario, contra, addPersonal}
    }
    // data() {
    //   return {
    //     nombre: "",
    //     email: "",
    //     aporte: "",
    //   };
    // },
    // methods: {
    //   addPersona() {
    //     if (this.nombre != "" && this.email != "") {
    //       const persona = {
    //         nombre: this.nombre,
    //         email: this.email,
    //         aporte: this.aporte,
    //       };
    //       this.$store.dispatch("addPersona", persona);
    //       this.$router.push('/print')
    //     }
    //   },
    // },
  };
  </script>