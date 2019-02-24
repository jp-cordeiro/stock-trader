<template>
<div>
    <h1 class="display-3 font-weight-light mb-4">Negocie e Consulte suas Ações</h1>

    <v-sheet :elevation="8" class="pa-2" color="primary">
        <v-icon class="white--text mr-3">info</v-icon>
        <span class="headline font-weight-light white--text">Você pode Salvar e Carregar os Dados</span>
    </v-sheet>

    <v-sheet :elevation="8" class="pa-2 mt-3 darken-1" color="success">
        <v-icon class="white--text mr-3">info</v-icon>
        <span class="headline font-weight-light white--text">Clique em 'Finalizar Dia' para iniciar um novo dia!</span>
    </v-sheet>
    <v-divider class="my-4"/>

    <p class="display-1">
        <b>
            Seu Saldo:
        </b>
        {{ funds }}
    </p>
</div>
</template>

<script>
    import { mapGetters } from 'vuex'

    export default {
        computed:{
            ...mapGetters(['funds'])
        }
    }
</script>

<style scoped>

</style>