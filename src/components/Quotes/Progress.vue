<template>
    <div class="progress">
      <div class="progress-bar" role="progressbar" :style="{ width: progress + '%' }" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100">{{ count }} / {{ limit }}</div>
    </div>	
</template>

<script>
	export default {
	    props: ['count', 'limit'],
	    computed: {
	        progress: function() {
	            return (this.count / this.limit) * 100;
	        }
	    }
	}
</script>