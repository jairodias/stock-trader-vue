<template>
    <v-flex class="pr-3 pb-3" xs12 md6 lg4>
        <v-card class="blue darken-3 white--text">
            <v-card-title class="headline">
                <strong>{{ stock.name }} 
                    <small>(Preço: {{stock.price | currency }} | Qtde: {{ stock.quantity }})
                    </small></strong>
            </v-card-title>
        </v-card>

        <v-card>
            <v-container fill-height>
                <v-text-field label="Quantidade" type="number" v-model.number="quantity" 
                    :error="insufficientQuantity || !Number.isInteger(quantity)"
                />
                <v-btn class="blue darken-3 white--text" 
                    :disabled="quantity <= 0 || !Number.isInteger(quantity) || insufficientQuantity"
                    @click="sellStock">{{insufficientQuantity ? 'Insuficiente' : 'Vender' }}</v-btn>
            </v-container>
        </v-card>
    </v-flex>
</template>

<script>
export default {
    props: ['stock'],
    computed: {
        insufficientQuantity() {
            return this.quantity > this.stock.quantity
        }
    },
    data() {
        return {
            quantity: 0
        }
    },
    methods: {
        sellStock() {
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            }
            
            this.$store.dispatch('sellStock', order)

            this.quantity = 0
        }
    }
}
</script>

<style scoped>

</style>