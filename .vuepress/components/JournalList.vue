<template>
  <div class="journal-list">
  	<div v-for="post in journal" :key="post.title" class="post">
  		<router-link tag="h2" :to="post.path" class="title">{{ post.frontmatter.title }}</router-link>
  		<p>{{ post.frontmatter.excerpt }}</p>
  		<p class="reading-time">{{post.readingTime.text}}</p>
  	</div>
  </div>
</template>

<script>
  export default {
  	computed: {
  		journal() {
  			return this.$site.pages
  				.filter(x => x.path.startsWith('/journal/') && !x.frontmatter.journal_index)
  				.sort((a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date))
  		}
  	}
  }
</script>

<style scoped>
	.journal-list {
		max-width: 700px;
		margin: auto;
	}
  .title {
    cursor: pointer;
		font-weight: 600;
		font-family: Canela;
		color: #1C3041;
		padding-bottom: .25rem;
  }
  .post {
		margin: 1rem;
    padding: 2rem 0;
    border-bottom: 1px solid #eee;
  }
  .post:last-of-type {
    border: 0;
  }
  .post h2 {
    margin: 0;
  }
  .post h2:hover {
    text-decoration: underline;
  }
  .post p {
    margin: 0;
    color: #555;
  }
	.reading-time {
		font-weight: 800;
		font-family: avenir;
		font-size:.9rem;
		padding-top: .5rem;
	}
</style>
