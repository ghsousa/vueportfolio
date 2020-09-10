<template>
<div class="carousel-div">
  <carousel :per-page="1" :navigate-to="someLocalProperty" :mouse-drag="true">
    <slide
      tag="div"
      v-for="post in posts"
      :key="post.title"
			@slideclick="handleSlideClick"
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
		methods: {
			handleSlideClick: function(dataset) {
    console.log(dataset.index, dataset.name)
  }
		},
  		computed: {
  			posts() {
  				return this.$site.pages
  					.filter(x => x.path.startsWith('/art/') && !x.frontmatter.works_index)
  					.sort((a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date))
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