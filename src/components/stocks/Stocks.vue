<template>
    <v-layout row wrap>
        <Stock v-for="stock in stocks" :key="stock.id"/>
    </v-layout>
</template>

<script>
    import Stock from "./Stock";

    export default {
        components:{ Stock },
        data(){
            return{
                stocks: [
                    { id: 1 , name: 'CD Projekt Red', price: 120},
                    { id: 2 , name: 'Insomniac Games', price: 150},
                    { id: 3 , name: 'Bandai', price: 200},
                    { id: 4 , name: 'Santa Monica Studios', price: 220},
                    { id: 5 , name: 'Nintendo', price: 215},
                ]
            }
        }
    }
</script>

<style scoped>

</style>