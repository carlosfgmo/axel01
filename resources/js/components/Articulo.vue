<template>
    <div>
        <h1 class="text-center">Mantenimiento de Articulos</h1>
        <hr>

        <table class="table table-striped">
            <thead class="table-dark">
                <tr>
                    <th>#</th>
                    <th>ARTICULO</th>
                    <th>DESCRIPCION</th>
                    <th>STOCK</th>
                    <th colspan="2">OPCIONES</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(articulo, indice) in articulos" :key="articulo.id">
                    <td>{{ indice + 1 }}</td>
                    <td>{{ articulo.nombre }}</td>
                    <td>{{ articulo.descripcion }}</td>
                    <td>{{ articulo.stock }}</td>
                    <td>
                        <button class="btn btn-warning">Editar</button>
                    </td>
                    <td>
                        <button class="btn btn-danger" @click="eliminar(articulo.id)">Eliminar</button>
                    </td>
                </tr>
            </tbody>
        </table>

    </div>
</template>

<script>
import axios from 'axios'

    export default {
        data() {
            return {
                articulos: [],
            }
        },
        methods: {
            async listar() {
                const response=await axios.get('/api/articulos');
                this.articulos = response.data.backend;
                // axios.get('/api/articulos')
                // .then( response => {
                //     this.articulos = response.data.backend
                // })
            },
            async eliminar(id) {
                const response=await axios.delete('/api/articulos/' + id);
                this.listar();
                // axios.delete('/api/articulos/' + id);
                // this.listar();
            }
        },
        created() {
            this.listar();
        },
    }
</script>

<style>

</style>