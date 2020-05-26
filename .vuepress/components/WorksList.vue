<template>
  <div class="project-list">
    <router-link
      :to="post.path"
      tag="div"
      v-for="post in posts"
      :key="post.title"
      class="post"
    >
      <div
        class="post_background"
        :style="{ backgroundImage: `url(${post.frontmatter.thumbnail})` }"
      ></div>

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

.post_background {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  width: 100%;
  height: 50vh;
  transition: all 1500ms cubic-bezier(0.25, 0.8, 0.25, 1);
}

.post:hover .post_background {
  transform: scale(1.1);
}

.post:hover .info {
	letter-spacing: 4px;
}

.info {
  position: absolute;
  left: 0;
  top: 2rem;
  padding: 0.5rem 1rem;
  background: rgba(255, 255, 255, 1);
  max-width: 400px;
	transition: all 1500ms cubic-bezier(0.25, 0.8, 0.25, 1);
	letter-spacing: 2px;
	text-transform: uppercase;
}

.info h2 {
  display: inline-block;
  width: auto;
  font-size: 1.3rem;
  font-weight: 700;
  margin: 0;
}

.info span {
  display: inline-block;
  width: auto;
  margin: 0;
  margin-left: 0.5rem;
  font-size: 0.8rem;
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
