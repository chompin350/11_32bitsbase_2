<template>
    <div class="container">
        <h1>Venta de Juegos</h1>
        <hr>
        <h4>Cantidad de juegos con stock: {{totaljuegos}}</h4>
        <hr>
        <table class="table table-bordered">
            <thead class="thead-dark">
                <tr>
                    <th>Codigo</th>
                    <th>Nombre</th>
                    <th>Stock</th>
                    <th>Precio</th>
                    <th>Venta</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(juego, index) in juegosConStock" :key="index">
                    <td>{{ juego.codigo }}</td>
                    <td>{{ juego.nombre }}</td>
                    <td>{{ juego.stock }}</td>
                    <td>{{ juego.precio }}</td>
                    <td><input type="button" value="Vender" @click="vender(juego)"></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import { mapActions, mapGetters, mapState} from "vuex";

export default {
    computed:{
         ...mapGetters(["juegosConStock","totaljuegos"]),
         ...mapState({
            totalVentas: (state) => {
                return `Total $ ${state.totalVentas}`;
            },
         }),
    
    },
    methods:{
        ...mapActions(['vender'])
    }
}
</script>