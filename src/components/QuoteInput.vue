<template>
    <div class="quote-input-container">
        <h3 class="heading3">Quote</h3>
        <textarea ref="quote" class="quote-input" id="" cols="10" rows="3" v-model="currentQuote" @keydown="addQuoteEnter"></textarea>
        <button class="btn-add" @click="addQuote">Add Quote</button>
    </div>
</template>

<script>
import {eventBus} from '../main';
export default {
    props: ['progress'],
    data() {
        return {
            currentQuote: ''
        }
    },
    methods: {
        addQuote() {
            if (this.currentQuote && this.progress<10) eventBus.$emit('addQuote', this.currentQuote);
            else if (this.progress===10 && this.currentQuote) alert('Quotes limit reached, delete some quotes to add more');
            this.currentQuote = '';
            this.$refs.quote.focus();
        },
        addQuoteEnter(e) {
            if (e.keyCode === 13) {
                this.addQuote();
                e.preventDefault();
            }
        }
        
    }
}
</script>

<style scoped>
    .quote-input-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        align-self: center;
        width: 38vw;
    }
    .quote-input {
        font-size: 2rem;
        font-family: sans-serif;
        font-weight: 400;
        align-self: stretch;
        margin-bottom: 1.5rem;
        border-radius: .5rem;
        padding: 1rem;
    }
    .heading3 {
        font-size: 1.6rem;
        align-self: flex-start;
    }
    .btn-add {
        background-color: #297fb9cc;
        color: #fff;
        font-weight: 600;
        padding: 1rem;
        margin-bottom: 1.5rem;
        border: .1rem solid #3498db;
        border-radius: .5rem;
        cursor: pointer;
        transition: all .2s;
    }
    .btn-add:hover {
        background-color: #3498dbe5;
    }
    .btn-add:active {
        background-color: #3498db9a;
    }
    .btn-add:focus {
        outline: none;
    }
</style>