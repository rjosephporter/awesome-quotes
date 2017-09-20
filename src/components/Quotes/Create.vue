<template>
	<form @submit.prevent="addQuote">
	    <div class="form-group">
	        <label for="quote">Enter quote:</label>
	        <textarea name="quote" id="quote" cols="30" rows="10" class="form-control" v-model="quote"></textarea>
	    </div>
	    <button class="btn btn-primary" type="submit">Submit</button>
	</form>
</template>

<script>
    import { quoteEventBus } from '../../main.js';

	export default {
	    props: ['quotes'],
	    data: function() {
	        return {
	            quote: ''
	        }
	    },
	    methods: {
	        addQuote: function() {
	            if(this.quotes.length >= 10) {
	              alert('Maximum number of quotes reached!');
	              return;
	            } 

	            var quoteData = {
	                quote: this.quote,
	                timestamp: new Date()
	            };
	            quoteEventBus.$emit('quoteAdded', quoteData);
	            this.quote = '';
	        }
	    }
	}
</script>