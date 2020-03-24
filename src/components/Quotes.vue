<template>
    <div class="quotes-container">
        <div class="quotes" v-for="(quote, i) in quotes" :data-position="i" :key="i" @click="deleteQuote">{{ quote }}</div>
    </div>
</template>

<script>
import {eventBus} from '../main';
export default {
    props: ['quotes'],
    created() {
        eventBus.$on('addQuote', (quote) => {
            this.quotes.push(quote);
        });
    },
    methods: {
        deleteQuote(e) {
            this.quotes.splice(e.target.dataset.position,1);
        }
    }
}
</script>

<style scoped>
    .quotes-container {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        column-gap: 2vw;
        row-gap: 2rem;
        margin-bottom: 2rem;
    }
    .quotes {
        /* font-family: Arizonia, 'Times New Roman'; */
        font-family:'Times New Roman', Times, serif;
        cursor: pointer;
        align-self: flex-start;
        padding: 1.3rem;
        font-size: 2.5rem;
        min-height: 6rem;
        max-width: 30rem;
        border: .1rem solid #ddd;
        border-radius: .5rem;
        background-color: #f1f2f641;
        transition: all .2s;
        word-wrap: break-word;
    }
    .quotes:hover {
        background-color: #fab1a050;
    }
</style>