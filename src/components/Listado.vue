<template>
    <div>
        <hr>
        <ul class="lista" >
        <li v-for="(juego, index) in filtro" :key="index">
            <div :style="{background: juego.color}">
                {{ juego.codigo }} | {{ juego.nombre }} | {{ juego.stock }} | {{ juego.precio }}
            </div>
        </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Listado',
    props:{
        filtro:{
            type: Array,
            required: false
        }
    }    
}
</script>

<style scope>
    
</style>