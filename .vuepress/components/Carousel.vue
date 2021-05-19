<template>
<div class="carousel-div">
  <carousel :per-page="1" :mouse-drag="true">
    <slide
      tag="div"
      v-for="post in posts"
      :key="post.title"
      class="post"
			>
    	<img class="work-img"  :src="post.frontmatter.thumbnail" />
    </slide>
  </carousel>
</div>
</template>

<script>
	import { Carousel, Slide } from 'vue-carousel';
  export default {
		components:{
			Carousel,
			Slide
		},
  		computed: {
  			posts() {
  				return this.path('/.vuepress/public/upload/photos/')
  			}
  		}
  	}
</script>

<style scoped>
.carousel-div {
	margin-top: 15vh;
	margin-left: auto;
	margin-right: auto;
}

.work-img {
	max-width: 800px;
	display: block;
	margin: auto;
}
</style>