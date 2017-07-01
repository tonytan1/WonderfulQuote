<template>
    <div class="container">
        <app-header v-bind:quoteCount="quotes.length" v-bind:maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid v-bind:quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="col-sm-12 text-center">
            <div class="alert alert-info">Info: Click on a Quote to delete it.</div>
        </div>
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/Header.vue';

export default {
    data: function () {
        return {
            maxQuotes: 10,
            quotes: [
                'Just a quote see something'
            ]
        }
    },
    components: {
        appQuoteGrid: QuoteGrid,
        appNewQuote: NewQuote,
        appHeader: Header
    },

    methods: {
        newQuote(quote) {
            if (quote) {
                if (this.quotes.length < this.maxQuotes) {
                    this.quotes.push(quote);
                } else {
                    alert("quote list is full!");
                }
            } else {
                alert("quote content required!")
            }

        },

        deleteQuote(index) {
            this.quotes.splice(index, 1);
        }
    }
}
</script>

<style>

</style>
