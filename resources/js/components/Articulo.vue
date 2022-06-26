<template>
    <div>
        <h1 class="text-center">Mantenimiento de Articulos</h1>
        <hr>

        <table class="table">
            <thead class="table-dark">
                <tr>
                    <th>#</th>
                    <th>ARTICULO</th>
                    <th>DESCRIPCION</th>
                    <th>STOCK</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(articulo, indice) in articulos" :key="articulo.id">
                    <td>{{ indice + 1 }}</td>
                    <td>{{ articulo.nombre }}</td>
                    <td>{{ articulo.descripcion }}</td>
                    <td>{{ articulo.stock }}</td>
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
        mounted() {
            axios
            .get('/api/articulos')
            .then(response => {
                this.articulos = response.data.backend,
                console.log(this.articulos)
            })
            .catch(error => {
                console.log(error)
            })
        },
        // methods: {
        //     async listar () {
        //         const res=await axios.get('articulos');
        //         this.articulos = res.data;
        //         console.log(res.data);
        //     }
        // },
        // created() {
        //     this.listar();
        // }
    }
</script>

<style>

</style>