<template>
  <div class="container">
  <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="quoteNew"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import NewQuote from './components/NewQuote.vue'
import Header from './components/Header.vue'

export default {
  data: function(){
    return {
      quotes: [
        'This is a test'
      ],
      maxQuotes: 10
    }
  },
  methods: {
    quoteNew(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        alert("Please delete some quotes before adding again!");
      }
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  }
}
</script>

<style>
</style>
