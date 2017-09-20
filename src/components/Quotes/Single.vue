<template>
    <div class="col-sm-4" @click="removeQuote(quoteIndex)">
        <div class="card text-white bg-info mb-3" style="max-width: 20rem;">
          <div class="card-body">
            <h4 class="card-title">{{ quote.quote }}</h4>
            <p class="card-text"></p>
          </div>
        </div>
    </div>
</template>

<script>
    import { quoteEventBus } from '../../main.js';

	export default {
	    props: ['quote', 'quoteIndex'],
	    methods: {
	        removeQuote: function(key) {
	            quoteEventBus.$emit('quoteRemoved', key);
	        }
	    }
	}
</script>