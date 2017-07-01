<template>
    <div class="row">
        <appQuote v-for="quote in quotes" @click.native="deleteQuote"> {{ quote }}</appQuote>
    </div>
</template>

<script>
import Quote from './Quote.vue';

export default {
    props: ['quotes'],
    components: {
        appQuote: Quote
    },
    methods: {
        deleteQuote(index) {
            this.$emit('quoteDeleted', index);
        }
    }
}
</script>
<style>

</style>