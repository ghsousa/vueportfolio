<template>
  <div class="project-list">
    <router-link
      :to="post.path"
      tag="div"
      v-for="post in posts"
      :key="post.title"
      class="post"
    >
		<img class="work-img"  :src="post.frontmatter.thumbnail" />
    </router-link>
  </div>
</template>

<script>
  export default {
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

	.project-list {
		display: grid;
		margin-top: 20vh;
		margin: auto;
		padding-bottom: 3rem;
		grid-gap: 10px;
		max-width: 1200px;
	}
	.post:hover .work-img {
		transform: translateY(-2%);
		box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);

	}
	.post:nth-child(2) {
		grid-column: 3;
		grid-row: 1 / 3;
	}
	.post:nth-child(2) .work-img {
		object-fit: cover;
	}
	.work-img {
		width: 100%;
		height: 100%;
		margin: 0;
				transition: all 500ms cubic-bezier(0.25, 0.8, 0.25, 1);
		box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
	}

  .info {
    position: absolute;
    left: 0;
    top: 2rem;
    padding: 0.5rem 1rem;
    max-width: 400px;
  }
  .info h2 {
		font-family: canela;
    display: none;
    width: auto;
    font-size: 4rem;
    font-weight: 700;
    margin: 0;
		color: #fff;
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
		.post:nth-child(2) {
		grid-column: 1;
		grid-row: 1 / 1;
	}
}
</style>