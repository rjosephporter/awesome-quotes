<template>
	<form @submit.prevent="addQuote">
	    <div class="form-group">
	        <label for="quote">Enter quote:</label>
	        <textarea name="quote" id="quote" cols="30" rows="10" class="form-control" v-model="quote"></textarea>
	    </div>
	    <button class="btn btn-primary" type="submit">Add Quote</button>
	</form>
</template>

<script>
	export default {
	    props: ['quotes'],
	    data: function() {
	        return {
	            quote: ''
	        }
	    },
	    methods: {
	        addQuote: function() {
	            var quoteData = {
	                quote: this.quote,
	                timestamp: new Date()
	            };
	            this.$emit('quoteAdded', quoteData);
	            this.quote = '';
	        }
	    }
	}
</script>