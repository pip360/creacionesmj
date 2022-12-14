<template>
<center>
 <div :style="mainStyle"> 
  <form v-on:submit.prevent="login">
    <center><img class="logo" src="../assets/img/logoCMJ.png"></center>
    <div class="form-group">
    <input
    v-model="nombreusuario"
     type="text"
     name="username"
     class="form-control1"
     placeholder="Usuario"
     :style="input"
     /> 
    </div>
    <div class="form-group">
    <input
    v-model="password"
     type="password"
     name="password"
     class="form-control1"
     placeholder="Contraseña"
     :style="input"
     />
     </div>
     <div class="form-group">
     <button class="btn btn-primary" @click="buscarUsuario">
       Ingresar
    </button>
     </div>
    </form>
</div></center>
</template>




<script>
import { ref } from 'vue'
import axios from 'axios'
import { useRouter } from 'vue-router';

export default {
    name: "Login",

    data(){
      return{
       router : useRouter(),
       usuarios : ref([]),
       nombreusuario : ref(""),
        password : ref(""),
      }


    },

    props:{
        mainStyle: String,
        inpuStyle: String,
    },

    methods: {
        buscarUsuario(){
            axios.get('https://creaciones-maria-jose-default-rtdb.firebaseio.com/persona.json')
            .then(res=>{
                console.log(res);
console.log(this.nombreusuario ,"usuario")
console.log(this.nombreusuario ,"password")
              for(const id in res.data){

                if(res.data[id].nombreusuario === this.nombreusuario && res.data[id].contra === this.password){
                    this.usuarios.push({
                        id: id,
                        nombre: res.data[id].nombre,
                        password: res.data[id].password,
                    })
                }
              }
              if(this.usuarios.length >=1){
                this.$store.state.mostrar = true
                /* this.router.push("/regisLog") */
              }else{
                alert("Usuario y Contraseña incorrecto")
              }
              this.usuarios.value= [];
            })
            .catch(error => console.log(error))
        }
    }
};
</script>
