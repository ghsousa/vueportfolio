<template>
  <div class="project-list">
    <router-link
      :to="post.path"
      tag="div"
      v-for="post in posts"
      :key="post.title"
      class="post"
    >

			<img class="post_image" :src="post.frontmatter.thumbnail" loading="lazy" />

      <!-- <div class="info">
        <h2>{{ post.frontmatter.title }}</h2>
      </div> -->
    </router-link>
  </div>

	
</template>

<script>
export default {
  computed: {
    posts() {
      return this.$site.pages
        .filter(x => x.path.startsWith("/works/") && !x.frontmatter.works_index)
        .sort(
          (a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
        );
    }
  }
};
</script>

<style scoped>
.project-list {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
	grid-template-rows: 1fr 1fr;
  margin: auto -5vw;
}

.post {
  position: relative;
  cursor: pointer;
  overflow: hidden;
  transition: all 1500ms cubic-bezier(0.25, 0.8, 0.25, 1);
}

.post_image {
	height: 100%;
	width: 100%;
	margin: 0;
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
