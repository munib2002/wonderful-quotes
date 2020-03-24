<template>
    <div class="container">
        <app-header :progress="quotes.length"></app-header>
        <app-quote-input :progress="quotes.length"></app-quote-input>
        <app-quotes :quotes="quotes"></app-quotes>
        <app-delete-info></app-delete-info>
    </div>
</template>

<script>
    import Header from './components/Header.vue';
    import QuoteInput from './components/QuoteInput.vue';
    import Quotes from './components/Quotes.vue';
    import DeleteInfo from './components/DeleteInfo.vue';
    export default {
        data() {
            return {
                quotes: ['Just a Quote to start with something!'],
            }
        },
        methods: {

        },
        components: {
            appHeader: Header,
            appQuoteInput: QuoteInput,
            appQuotes: Quotes,
            appDeleteInfo: DeleteInfo
        }
    }
</script>

<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: inherit;
    }
    html {
        font-size: 62.5%;
        box-sizing: border-box;
    }
    body {
        font-size: 1.6rem;
        font-family: sans-serif;
        line-height: 1.6;
        font-weight: 400;
    }
    .container {
        margin: 5vh 7vw;
        display: flex;
        flex-direction: column;
    }
</style>
