<template>
    <v-layout row wrap>
        <Stock v-for="stock in stocks" :key="stock.id" :stock="stock" />
    </v-layout>
</template>

<script>

import Stock from './Stock'

export default {
    components: {
        Stock
    },
    data() {
        return {
            stocks: [
                {id: 1, name: 'BMW', price: 110},
                {id: 2, name: 'Twitter', price: 200},
                {id: 3, name: 'Google', price: 300},
                {id: 4, name: 'Facebook', price: 280},
                {id: 5, name: 'Instagram', price: 110},
            ]
        }
    }
}
</script>

<style scoped>

</style>