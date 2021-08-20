<template>
  <div id="app">
    
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div id="navbarNav" style="margin: 0 auto;">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link">
              <router-link :to="{name: 'inicio'}">Inicio</router-link>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link">
              <router-link :to="{name: 'busqueda'}">Busqueda</router-link>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link">
              <router-link :to="{name: 'ventas'}">Ventas</router-link>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link">
              <router-link :to="{name: 'total'}">Total</router-link>
            </a>
          </li>
        </ul>
      </div>
    </nav>
    <div class="container">
      <h1>{{titulo}}</h1>
      <h2>{{subtitulo}}</h2>
    </div>
    <hr>
    <transition name="vista">
      <router-view></router-view>
    </transition>
  </div>
</template>

<script>
import { mapState} from "vuex";

export default {
  data(){
    return {
      
    }
  },
  computed:{
    ...mapState({
      titulo: (state) => {
        return state.titulo;
      },
      subtitulo: (state) => {
        return state.subtitulo;
      }
    }),
    totaljuegos(){
      return this.$store.state.juegos;
    }
  }
  
}
</script>

<style scoped>

.container{
  text-align: center;
}
.vista-enter-active, .vista-leave-active {
    transition: opacity .1s;
}
.vista-enter, .vista-leave-to{
    opacity: 0;
}

.navbar{
  display: flex;
  background-color: #333;
}

.navbar a{
  color: white;
  padding: 14px 20px;
  text-decoration: none;
  text-align: center;
}

.navbar a:hover{
  background-color: #ddd;
  color: black;
}

</style>
