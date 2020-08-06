<template>

<div class="movie-container">
<router-link to="/about/">
<video width="100%" height="100%" autoplay loop muted> 
  <source src="/upload/intro.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
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
	max-width: 800px;
}

video {
	margin: auto;
		display: block;
}
</style>