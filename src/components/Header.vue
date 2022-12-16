<template>
  <nav class="navbar navbar-light nav-pills" style="background: linear-gradient(to right, #e69ded 8%, #e69ded 100%);">
    <div class="con1"> 
      <ul class="nav">
        <img src="../assets/img/logoCMJ.png" class="imagen_menu"/>
        <li class="nav-item">
          <router-link to="/log" class="nav-link" active-class="active"
            >INICIAR SESION</router-link
          >
          <img src="../assets/img/perfil-del-usuario.png" alt="iniciar sesion" class="sesion">
        </li>
        <li class="nav-item" v-if="verificar">
          <router-link to="/home" class="nav-link" active-class="active"
            >Home</router-link
          >
          <img src="../assets/img/home-icon.png" class="casa-icon">
        </li>
        <li class="nav-item" v-if="verificar">
          <router-link to="/pedidos" class="nav-link" active-class="active"
            >Hacer Pedido</router-link
          >
        </li>

        <li class="nav-item" v-if="verificar">
          <router-link to="/prod" class="nav-link" active-class="active"
            >Añadir Productos</router-link
          >
        </li>
        <li class="nav-item" v-if="verificar">
          <router-link to="/regislog" class="nav-link" active-class="active"
            >Añadir Usuarios</router-link
          >
        </li>

        <li class="nav-item" v-if="verificar">
          <router-link to="/perso" class="nav-link" active-class="active"
            >Añadir Personal </router-link
          >
        </li>
        <li class="nav-item" v-if="verificar">
          <router-link to="/print" class="nav-link" active-class="active"
            >Productos</router-link
          >
        </li>
        <li class="nav-item" v-if="verificar">
          <router-link to="/persoData" class="nav-link" active-class="active"
            >Personal</router-link
          >
        </li>
        <li class="nav-item" v-if="verificar">
          <a class="nav-link" href="./log">Cerrar Sesion</a>
          <img src="../assets/img/poder.png" alt="cerrar sesion" class="sesion">
        </li>
      </ul>
    </div>
  </nav>

</template>

<script>
export default {
  data(){
    return{
      error:false,
      mostrar: this.$store.state.mostrar
    }
  },
  computed:{
    verificar(){
      return this.$store.state.mostrar
    },
  },
}

</script>

<style>
a{
color:rgb(10, 10, 10)
}
a.nav-link{
color:rgb(255, 255, 255);
}
a:hover{
  color:rgb(228, 74, 233);
  text-decoration: none;
  }
.nav-pills .nav-link.active, .nav-pills .show > .nav-link{
  color: rgb(255, 255, 255);
  background-color: #edb6f1;
  border-color: #e69ded;
}

.form-control1{
  color: #FFF;
  background-color: #e69ded;
  border-color: #000000;
  width: 50%;
  display: block;
  height: calc(1.5em + 0.75rem + 2px);
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  background-clip: padding-box;
  border: 1px solid #e69ded;
    border-radius: 0.25rem;
    transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
  
}

.btn-primary{
  color: #FFF;
  background-color: #e69ded;
  border-color: #e69ded
}
.btn-primary:hover{
  color: rgb(255, 255, 255);
  background-color:  #f47eff;
  border-color:  #e69ded;
}
.btn-primary:link{
  color: rgb(255, 255, 255);
  background-color:  #e69ded;
  border-color:  #e69ded;
}
.btn-primary:active{
  color: rgb(255, 255, 255);
  background-color:  #e69ded;
  border-color:  #e69ded;
}
.logo{
  width:500px,
}
.imagen_menu{
display:block;
height: 40px;
}
.sesion{
  max-width: 50px;
  margin: 1rem 3rem;
}
.nav img{
  max-width: auto;
}
.casa-icon{
max-width: 50px;
margin: 1rem 3rem;
}
.nav-item{
  text-align: center;
}

</style>