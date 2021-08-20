<template>
    <div class="container">
        <div class="total">
            <h2>Monto total de ventas <span class="venta"> {{formatPrice(totalVentas)}} </span> </h2>
        </div>
        <hr>
        <h4>Detalle total de Ventas</h4>
        <table class="table table-bordered">
            <thead class="thead-dark">
                <tr>
                    <th>Codigo</th>
                    <th>Nombre</th>
                    <th>Precio</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(juego, index) in ventasEfectuadas" :key="index">
                    <td>{{ juego.codigo }}</td>
                    <td>{{ juego.nombre }}</td>
                    <td>{{ formatPrice(juego.precio) }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    computed:{
        totalVentas() {
            return this.$store.state.totalVentas;
        },
        ventasEfectuadas(){
            return this.$store.state.ventas;
        }

    },
    methods:{
        formatPrice(value) {
            let val = (value/1)
            return '$ ' + val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".")
        },
    }
    
}
</script>

<style scoped>

.venta{
    color:blue;
}
</style>