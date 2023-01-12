<template>
    <div classname="background-img" v-for="quote in quotes" :key="quote.id">
        <ul>
            <li>{{ quote.quote }}</li>
            <li>{{ quote.author }}</li>
        </ul>
    </div>
    <button @click="getRandomQuote" class="btn btn-secondary">
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
            const id = Math.floor(Math.random() + 1);
            fetch(`https://api.breakingbadquotes.xyz/v1/quotes/${id}`)
            .then(response => response.json())
            .then(data => {
                this.quotes = data;
            });
        }
    }
}
</script>

<style>

li {
    list-style: none;
    color: #fff;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 24px;
}
body {
    background-image: url('../assets/thumb-1920-851514.jpg');
    background-size: cover; /* establece el tamaño de la imagen para cubrir todo el elemento */
    background-repeat: no-repeat; /* evita que la imagen se repita */
}

</style>