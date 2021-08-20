<template>
  <div class="container">
    <div class="filtro">
        <h4>Busqueda de Productos Disponibles</h4>
        <input type="text" v-model="codigoid">
        <hr />
    </div>
    <h5>Cantidad de juegos totales :  {{totaljuegos}}</h5>
    <hr>
    <h5>Cantidad de stock total de juegos : {{stocktotal}}</h5>
    <Listado
      :filtro="searfiltro">
    </Listado>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import Listado from './Listado'
export default {
    data(){
        return {
         codigoid: ''
        }
    },
    components:{
      Listado
    },
    computed: {
        ...mapGetters(['juegosConStock','totaljuegos','stocktotal']),
        searfiltro(){
            return this.$store.getters.filtrojuegos(this.codigoid)
        }
    },
};
</script>

<style scope>
input {
  text-align: center;
}
.lista{
    text-align: left;
}
</style>