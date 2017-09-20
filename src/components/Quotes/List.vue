<template>
	<div class="row">
	    <quote-single v-for="(quote, ndx) in quotes" :key="ndx" @click.native="removeQuote(ndx)" :quoteIndex="ndx">{{ quote.quote }}</quote-single>
	</div>
</template>

<script>
    import QuoteSingle from './Single.vue';
	
	export default {
	    props: {
	        quotes: Array
	    },
	    methods: {
	        removeQuote: function(key) {
	            this.$emit('quoteRemoved', key);
	        }	    	
	    },
	    components: {
	        'quote-single': QuoteSingle 
	    }
	}
</script>