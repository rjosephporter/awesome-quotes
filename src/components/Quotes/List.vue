<template>
	<div class="row">
	    <quote-single v-for="(quote, ndx) in quotes" :key="ndx" :quote="quote" :quoteIndex="ndx"></quote-single>
	</div>
</template>

<script>
    import QuoteSingle from './Single.vue';
	
	export default {
	    props: {
	        quotes: Array
	    },
	    components: {
	        'quote-single': QuoteSingle 
	    }
	}
</script>