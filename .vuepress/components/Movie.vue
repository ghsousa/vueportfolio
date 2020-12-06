<template>

<div class="movie-container">
<router-link to="/about/">
<img  src="/upload/intro.gif" >
</router-link>
</div>

</template>

<script>
export default {
	mounted: function(){}
	}
</script>

<style scoped>
.movie-container {
	margin: auto;
	max-width: 600px;
}

img {
	margin: auto;
	display: block;
	
}
</style>