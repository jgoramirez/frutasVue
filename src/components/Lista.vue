<template>
    <div>
        <ul class="list-group">
            <li v-for="(item,index) of arrayOrdenar" :key="item.id" @click="aumentar(index)" class="list-group-item d-flex justify-content-between align-items-center">
                {{item.id}} - {{item.nombre}}
                <span class="badge badge-primary badge-pill">{{item.cantidad}}</span>
            </li>
        </ul>
        <button @click="reiniciar" class="btn btn-danger btn-block">Reiniciar</button>
    </div>
</template>

<script>

import {mapState, mapMutations} from 'vuex'

export default {
    name:'Lista',
    computed: {
        ...mapState(['frutas']),
        arrayOrdenar() {
            return this.frutas.sort((a, b) => b.cantidad - a.cantidad)
        }
    },
    methods: {
        ...mapMutations(['aumentar', 'reiniciar'])
    }
}
</script>