<template>
<center>
    <div class="con">
      
      <h3>Registro de Pedidos</h3>
  
      <div class="card" style="width: 35rem">
        <div class="card-body">
          <h5 class="card-title">Productos</h5>
  <br>
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
            <label for="formGroupExampleInput2">Nombre</label>
            <input
              v-model="nombrepedido"
              type="text"
              class="form-control"
              placeholder="Multiusos/Pijama"
            />
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
          <div class="form-group">
            <label for="formGroupExampleInput2">Cantidad</label>
            <input
              v-model="cantidad"
              type="text"
              class="form-control"
              placeholder="1-20"
            />
          </div>

          <div class="form-group">
            <label for="formGroupExampleInput2">Medio de pago</label>
            <select name="Medio de pago"
            v-model="pago"
            class="form-control">
              <option value="0">Seleccione una opción</option>
              <option value="">Nequi</option>
              <option value="">Efectivo</option>
            </select>
          </div>
<hr>
          <h5 class="card-title">Datos Personales</h5>
<br>
          <div class="form-group">
            <label for="formGroupExampleInput2">Nombre Completo</label>
            <input
              v-model="nombrecliente"
              type="text"
              class="form-control"
              placeholder="Juan Smith"
            />
          </div>

          <div class="form-group">
            <label for="formGroupExampleInput2">Numero de identificacion</label>
            <input
              v-model="cedula"
              type="text"
              class="form-control"
              placeholder="1082..."
            />
          </div>

          <div class="form-group">
            <label for="formGroupExampleInput2">Telefono</label>
            <input
              v-model="telefono"
              type="text"
              class="form-control"
              placeholder="310-000-0000"
            />
          </div>

          <div class="form-group">
            <label for="formGroupExampleInput2">Correo</label>
            <input
              v-model="correo"
              type="text"
              class="form-control"
              placeholder="hola@gmail.com"
            />
          </div>

          <div class="form-group">
            <label for="formGroupExampleInput2">Fecha</label>
            <input type="DATE" name="fecha-n"
            v-model="fecha"
              class="form-control"
              
            />
          </div>

          <div class="form-group">
            <label for="formGroupExampleInput2">Direccion</label>
            <input
              v-model="direccion"
              type="text"
              class="form-control"
              placeholder="cll 6, Piedecuesta, Santander"
            />
          </div>
          
          <button class="btn btn-primary" @click="addPedidos">
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
      const codigo = ref("")
      const nombrepedido = ref("")
      const precio = ref("")
      const cantidad = ref("")
      const pago = ref("")
      const nombrecliente = ref("")
      const cedula = ref("")
      const correo = ref("")
      const telefono = ref("")
      const direccion = ref("")
      const fecha = ref("")



      
      function addPedidos(){
        if(codigo.value != "" && nombrepedido.value != "" && precio.value != "" && cantidad.value != "" && pago.value != "" && nombrecliente.value != "" && cedula.value != "" && correo.value != "" && telefono.value != "" && direccion.value != "" && fecha.value != ""){
          const pedido = {
            codigo:codigo.value,
            nombrepedido:nombrepedido.value,
            precio:precio.value,
            cantidad:cantidad.value,
            pago:pago.value,
            nombrecliente:nombrecliente.value,
            cedula:cedula.value,
            correo:correo.value,
            telefono:telefono.value,
            direccion:direccion.value,
            fecha:fecha.value,
          }
          /* store.dispatch("addPersona", persona);
          router.push('/print') */
          axios.post('https://creaciones-maria-jose-default-rtdb.firebaseio.com/pedido.json',pedido)
          .then(res => console.log(res))
          .catch(error => console.log(error))
        }
      }
  
      return{codigo, nombrepedido, precio, cantidad, pago, nombrecliente, cedula, correo, telefono, direccion, fecha, addPedidos}
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
  <style>
  .card {
    background-color: rgb(240, 125, 255);
  }
    
  </style>