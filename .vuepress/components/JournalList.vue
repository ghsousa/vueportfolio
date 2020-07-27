<template>
  <div class="journal-list">
  	<div v-for="post in journal" :key="post.title" class="post">
			<router-link tag="h2" :to="post.path">
			<div class="post-content">
  		<h2 class="title">{{ post.frontmatter.title }}</h2>
  		<p class="excerpt">{{ post.frontmatter.excerpt }}</p>
  		<p class="reading-time">{{post.readingTime.text}}</p>
			</div>
			</router-link>
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
		},
		methods:{
			backgroundColor() {
				let colors = ['#f3dcbe', '#bde9d3', '#c0bde9'];
				let post = document.getElementsByClassName("post");
				let i;
				for (i = 0; i < post.length; i++) {
					// post[i].style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
				}
			}
		},
		mounted() {
			this.backgroundColor()
		}
  }
</script>

<style scoped>
	.journal-list {
		display: grid;
		grid-gap: 10px;
		margin-top: 20vh;
		padding-bottom: 3rem;
	}

	.title {
		cursor: pointer;
		font-weight: 600;
		font-family: Canela;
		color: #000;
		padding-bottom: .25rem;
	}

	.excerpt {
		font-family: Chap;
		font-size: 1.1rem;
		letter-spacing: .2px;
	}

	.post {
		margin: .25rem;
		padding: 2rem;
		/* border-bottom: 1px solid #eee; */
		background: #3adbc0;
		transition: all 500ms cubic-bezier(0.25, 0.8, 0.25, 1);
		box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
	}

	.post:nth-child(2n+1) {
		background: #ffa69a;
	}

		.post:nth-child(3n+1) {
		background: #99ceff;
	}


	.journal-list .post:nth-child(2) {
		grid-column: 2;
		grid-row: 2 / 4;
	}

	.journal-list .post:nth-child(1) {
		grid-column: 3 / 3;
		grid-row: 1 / 3;
		box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
	}

	.post:hover {
		transform: translateY(-2%);
		box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
	}

	.post:nth-child(1) {
		background-image: url('/upload/journalbg.jpg');
		background-size: cover;
		background-attachment: fixed;
		background-repeat: no-repeat;
		background-position: bottom;
		background-color: #fdbda4;
	}

	.post:nth-child(1) .title {
		font-size: 4rem;
	}
	.post:nth-child(1) .excerpt {
		font-size: 1.75rem;
		color: #fff;
	}

	.post:last-of-type {
		border: 0;
	}

	.post h2 {
		margin: 0;
	}

	.post h2:hover {
		cursor: pointer;
	}

	.post p {
		margin: 0;
		color: #000;
	}

	.reading-time {
		font-weight: 800;
		font-family: avenir;
		font-size: .9rem;
		padding-top: .5rem;
	}

	@media screen and (max-width: 1000px) {
		.journal-list {
			margin-top: 20vh;
		}

		.journal-list .post:nth-child(5) {
			grid-column: 1 / 1;
			grid-row: 1 / 4;
		}

		.post:nth-child(5n) {
			background-size: cover;
			background-position: -200px;
		}

	}

	@media screen and (max-width: 728px) {
		.journal-list {
			display: block;
		}

		.journal-list .post:nth-child(1) {
			grid-column: 1fr;
			grid-row: 1fr;
			background-image: none;
		}

	 .post:nth-child(1) .title {
		font-size: 2rem;
	}
		.post:nth-child(2) p {
		font-size: 1.25rem;
	}
	}

</style>
