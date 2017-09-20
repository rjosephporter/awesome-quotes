<template>
  <div class="container">
    <div class="row mt-3">
      <h1 class="text-center">Awesome Quotes</h1>
    </div>
    <div class="row mt-3 mb-3">
      <div class="col">
        <quote-progress :count="count" :limit="limit"></quote-progress>  
      </div>
    </div>
    <div class="row mb-3">
      <div class="col">
        <quote-create :quotes="quotes" @quoteAdded="addQuote"></quote-create>
      </div>
    </div>
    <div class="row mb-3">
      <div class="col">
        <quote-list :quotes="quotes" @quoteRemoved="removeQuote"></quote-list>
      </div>
    </div>
    <div class="row mb-3">
      <div class="col">
        <div class="alert alert-info" role="alert">
          Info: Click on quote to delete it
        </div>        
      </div>
    </div>
  </div>
</template>

<script>
  import QuoteProgress from './components/Quotes/Progress.vue';
  import QuoteCreate from './components/Quotes/Create.vue';
  import QuoteList from './components/Quotes/List.vue';
  import { quoteEventBus } from './main.js';
  
  export default {
    data () {
      return {
        quotes: [
          { 'quote': 'This is a test quote', 'timestamp': '123456' },
          { 'quote': 'Second quote coming up!', 'timestamp': '654321' }
        ],
        limit: 10
      };
    },
    computed: {
      count: function() {
        return this.quotes.length;
      }
    },
    components: {
      'quote-progress': QuoteProgress,
      'quote-create': QuoteCreate,
      'quote-list': QuoteList
    },
    methods: {
      addQuote: function(quote) {
        
        if(this.quotes.length >= this.limit) {
          alert('Maximum number of quotes reached!');
          return;
        }         
        
        this.quotes.unshift(quote);
      },
      removeQuote: function(index) {
        this.quotes.splice(index, 1);
      }
    }
  }
</script>

<style>

</style>
