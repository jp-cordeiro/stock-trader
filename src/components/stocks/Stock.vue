<template>
    <v-flex class="pr-3 pb-3" xs12 md6 lg4>
        <v-card class="green darken-3 white--text">
            <v-card-title class="headline">
                <b> {{ stock.name }} <small> (Preço: {{ stock.price | currency }} )</small></b>
            </v-card-title>
        </v-card>
        <v-card>
            <v-container fill-height>
                <v-text-field
                        label="Quantidade"
                        type="number"
                        :error="insuficientFunds || !Number.isInteger(quantity)"
                        v-model.number="quantity"/>
                <v-btn class="green darken-3 white--text"
                       :disabled=" insuficientFunds || quantity <= 0 || !Number.isInteger(quantity)"
                       @click="buyStock">{{ insuficientFunds ? 'Saldo insuficiente' : 'Comprar' }}</v-btn>
            </v-container>
        </v-card>
    </v-flex>
</template>

<script>
    export default {
        props: ['stock'],
        data(){
            return{
                quantity: 0
            }
        },
        computed: {
            funds(){
                return this.$store.getters.funds
            },
            insuficientFunds(){
                return this.quantity * this.stock.price > this.funds
            }
        },
        methods:{
            buyStock(){
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                }

                this.$store.dispatch('buyStock', order)

                this.quantity = 0
            }
        }
    }
</script>

<style scoped>

</style>