<template>
  <div class="project-list">

    <router-link
      :to="post.path"
      tag="div"
      v-for="post in posts"
      :key="post.title"
      class="post"
      :style="{ backgroundImage: `url(${post.frontmatter.thumbnail})` }"
    >

      <div class="info">
        <h2>{{ post.frontmatter.title }}</h2>
        <span v-if="post.frontmatter.description">{{ post.frontmatter.description }}</span>
      </div>

    </router-link>

  </div>
</template>

<script>
  export default {
    computed: {
      posts() {
        return this.$site.pages
          .filter(x => x.path.startsWith('/works/') && !x.frontmatter.works_index)
          .sort((a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date))
      }
    }
  }
</script>

<style scoped>

	.project-list {
		display: grid;
		grid-template-columns: 1fr 1fr;
		column-gap: 3rem;
		row-gap: 3rem;
		max-width: 1200px;
		margin: auto;
	}

  .post {
    position: relative;
    width: 100%;
    height: 50vh;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    cursor: pointer;
	  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
  	transition: all 0.3s cubic-bezier(.25,.8,.25,1);
  }

	.post:hover {
		 box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
	}

  .info {
    position: absolute;
    left: 0;
    top: 2rem;
    padding: 0.5rem 1rem;
    background: rgba(255,255,255, 1);
    max-width: 400px;
		box-shadow: 7px 7px 0px #000;
  }

  .info h2 {
    display: inline-block;
    width: auto;
    font-size: 1.5rem;
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

	@media only screen and (max-width: 728px) {
		.project-list {
			grid-template-columns: 1fr;
		}
}

</style>
