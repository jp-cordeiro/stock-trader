<template>
    <v-flex class="pr-3 pb-3" xs12 md6 lg4>
        <v-card class="blue darken-3 white--text">
            <v-card-title class="headline">
                <b>
                    {{ stock.name }}
                    <small> (Preço: {{ stock.price | currency }} | Qtd: {{ stock.quantity }})</small>
                </b>
            </v-card-title>
        </v-card>
        <v-card>
            <v-container fill-height>
                <v-text-field
                        label="Quantidade"
                        type="number"
                        :error="insuficenteQuantity || !Number.isInteger(quantity)"
                        v-model.number="quantity"/>
                <v-btn class="blue darken-3 white--text"
                       :disabled=" insuficenteQuantity || quantity <= 0 || !Number.isInteger(quantity)"
                       @click="sellStock">{{ insuficenteQuantity ? 'Quantidade insuficiente' : 'Vender' }}</v-btn>
            </v-container>
        </v-card>
    </v-flex>
</template>

<script>
    import { mapActions } from 'vuex'

    export default {
        props: ['stock'],
        data(){
            return{
                quantity: 0
            }
        },
        computed:{
            insuficenteQuantity(){
                return this.quantity > this.stock.quantity
            }
        },
        methods:{
            ...mapActions({
                sellStockAtion: 'sellStock'
            }),
            sellStock(){
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                }

                this.sellStockAtion(order)
                //this.$store.dispatch('sellStock', order)

                this.quantity = 0
            }
        }
    }
</script>

<style scoped>

</style>