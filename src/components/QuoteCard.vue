<template>
    <div v-for="quote in quotes" :key="quote.id">
        <ul>
            <li>{{ quotes.quote }}</li>
            <li>{{ quotes.author }}</li>
        </ul>
    </div>
    <button @click="getRandomQuote">
        Get Quote
    </button>
</template>

<script>
export default {
    data() {
        return {
            quotes: [],
            id: '',
        }
    },
    methods: {
        getRandomQuote() {
            const id = Math.floor(Math.random() * 101);
            fetch(`https://api.breakingbadquotes.xyz/v1/quotes/${id}`)
            .then(response => response.json())
            .then(data => {
                this.quotes = data[0];
            });
        }
    }
}
</script>

<style>

</style>