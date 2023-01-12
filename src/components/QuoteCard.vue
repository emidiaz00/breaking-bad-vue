<template>
    <div v-for="quote in quotes" :key="quote.id">
        <ul>
            <li>{{ quote.quote }}</li>
            <li>{{ quote.author }}</li>
        </ul>
    </div>
    <button @click="changeQuote()">
        Get Quote
    </button>
</template>

<script>
export default {
    data() {
        return {
            quotes: [],
            id: ''
        }
    },
    mounted() {
        fetch(`https://api.breakingbadquotes.xyz/v1/quotes/${this.id}`)
        .then(response => response.json())
        .then(data => 
        // asigna la respuesta a una propiedad de un component de vue
        this.quotes = data)
    },
    methods: {
        ramdomId() {
            this.id = Math.floor(Math.random() * 101)
        }
    }
}
</script>

<style>

</style>