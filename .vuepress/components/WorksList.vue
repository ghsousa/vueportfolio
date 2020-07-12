<template>
  <div class="project-list">
			<img v-for="post in posts" :key="post.title" class="post" :src="post.frontmatter.thumbnail" />
  </div>
</template>

<script>
export default {
  computed: {
    posts() {
      return this.$site.pages
        .filter(x => x.path.startsWith("/art/") && !x.frontmatter.works_index)
    }
  }
};
</script>

<style scoped>
.project-list {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr;
	column-gap: 4rem;;
	row-gap: 4rem;
	height: 100vh;
	width: 100vw;
	padding: 4rem;
}

.post {
	margin: 1rem;
	border-radius: 15px;
	margin: 0rem;

}

@media only screen and (max-width: 800px) {
  .project-list {
    grid-template-columns: 1fr;
  }
}

@media only screen and (max-width: 1169px) and (min-width: 800px) {
  .project-list {
    grid-template-columns: 1fr 1fr;
  }
}
</style>