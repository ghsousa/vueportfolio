<template>
  <div class="wrapper">
  	<div class="container">
  		<div v-if="$route.path === '/'">
  			<Content />
  		</div>
  		<div v-else-if="$route.path == '/art/'">
			<Navbar :logo="$site.themeConfig.logo" :sticky="$route.path === '/'" />
  			<Content />
  		</div>
			<div v-else-if="$route.path == '/about/'">
				<div class="about">
			  	<Content />
							<button type="button" @click="hasHistory() 
    ? $router.go(-1) 
    : $router.push('/')" class="my-5 btn btn-outline-success">&laquo;
  				Back
  			</button>
				<a href="mailto:gsousa09@gmail.com" id="about-mail">Let's talk.</a>
				</div>
			</div>



  		<!-- Single project view -->
  		<div v-if="isSingleProject" class="single-project">
  			<Content />
  			<SingleProjectHeader :title="$page.frontmatter.title" :year="$page.frontmatter.year.toString()"
  				:categories="$page.frontmatter.categories" />
  		</div>

  		<!-- Journal list -->
  		<div v-if="$route.path === '/journal/'" class="journal-list">
			<Navbar :logo="$site.themeConfig.logo" :sticky="$route.path === '/'" />
  			<Content />
							<button type="button" @click="hasHistory() 
    ? $router.go(-1) 
    : $router.push('/')" class="my-5 btn btn-outline-success">&laquo;
  				Back
  			</button>
  		</div>

  		<!-- Single journal -->
  		<div v-if="isSingleJournal" class="single-journal">
  			<h1 class="title">{{ $page.frontmatter.title }}</h1>
  			<Content />
  			<button type="button" @click="hasHistory() 
    ? $router.go(-1) 
    : $router.push('/')" class="my-5 btn btn-outline-success">&laquo;
  				Back
  			</button>
  		</div>

  	</div>

  </div>
</template>

<script>
  export default {
    computed: {
      isSingleProject() {
        const worksRoute = '/works/'
        const path = this.$route.path
        if (path.includes('works') && path.length >= (worksRoute.length + 1)) {
          return true
        }
      },
      isSingleJournal() {
        const journalRoute = '/journal/'
        const path = this.$route.path
        if (path.includes('journal') && path.length >= (journalRoute.length + 1)) {
          return true
        }
			}
    },
    updated() {
        // unwrap all images from paragraph tags so we can have
        // different widths inside the content.

        document.querySelectorAll('p img').forEach(image => {
          var wrapper = image.parentNode
          let children = wrapper.children
          let fragment = document.createDocumentFragment()

          Array.from(children).forEach(child => {
            fragment.appendChild(child)
          })

          wrapper.parentNode.replaceChild(fragment, wrapper)

        })
		},
	methods: {
		 hasHistory () { return window.history.length > 2 }
	}
	}
</script>

<style>

  :root {
    --color-black: #1c1c1c;
    --color-highlight: rgba(249, 233, 172, 0.99);
  }

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  *::-moz-selection {
    background: var(--color-highlight);
    color: var(--color-black);
  }

  *::-webkit-selection {
    background: var(--color-highlight);
    color: var(--color-black);
  }

  *::selection {
    background: var(--color-highlight);
    color: var(--color-black);
  }

  body {
		font-family: Canela;
    font-size: 1rem;
    background: #fff;
    color: #1C3041;
		font-weight: 500;
  }

  img {
    width: 100%;
    max-width: 100%;
    line-height: 0;
    margin: 2rem 0;
  }

 .single-journal, .journal-list .content__default  {
    width: 800px;
    max-width: 100%;
    margin: 0 auto;
  }

  h1,h2,h3,h4,h5,h6,p {
    width: 100%;
    max-width: 800px;
  }

  h1 {
    font-size: 3rem;
    line-height: 1.15;
    font-weight: 300;
    margin: 0 auto 3rem auto;
  }

  h2 {
    font-size: 2rem;
    font-weight: 300;
    margin: 2rem auto 2rem auto;
  }

  h3 {
    font-weight: 700;
    margin: 2rem auto 1rem auto;
  }
	h4 {
		font-weight: 300;
	}

  p {
    font-size: 1rem;
    line-height: 1.5;
    margin: 1rem auto 2rem auto;
		font-weight: 400;
  }

	a {
		transition: all ease-in-out .2s;
		text-decoration: none;
		color: #1C3041;
	}

	.single-journal {
		margin-top: 3rem;
		padding: 1rem 2rem;
	}

	.single-journal p {
		font-weight: 200;
		font-size: 1.3rem;
		line-height: 2;
		color: #444;
	}

	.single-journal .title {
		font-weight: 600;
		font-size: 7rem;
		text-align: left;
	}

	.single-project img {
		max-width: 680px;
		display: block;
		margin: auto;
	}

	.single-project .content__default {
		max-width: 680px;
		margin: auto;
	}

	.single-project h1 {
		font-weight: 600;
		margin-bottom: 0;
		margin-top: 3rem;
	}

	.about {
		max-width: 500px;
		margin: auto;
		border-radius: 10px;
		padding: 2rem ;
	}

	.about h1, .about p {
		margin: 0;
	}

	.about h1 {
		padding: 1rem 0;
	}

	.about p {
		font-weight: 200;
		font-size: 1.3rem;
		line-height: 2;
		color: #444;
	}

	#about-mail {
		margin-top: 2rem;
		font-size: 1.25rem;
		font-family: Canela;
		color: #1C3041;
		float: right;
		line-height: 1.3;
		letter-spacing: 2px;
	}

	#about-mail:hover {
		text-decoration: underline;
	}

	iframe {
		margin-top: 2rem;
		width: 100%;
	}

	button {
		margin-top: 2rem;
		background: #fff;
		border: none;
		font-size: 1.5rem;
		font-family: Canela;
		color: #1C3041;
	}

	pre {
		background: #0722bb10;
		border-radius: 5px;
		padding: 1rem;
		line-height: 1.75;
		overflow: scroll;
	}

	pre code {
		font-family: menlo;
	}

	 .single-journal ul {
		margin: auto;
		padding: 1rem;
		line-height: 2;
		font-size: 1rem;
		border-radius: 5px;
		background: rgba(238, 238, 238, 0.267);
	}

	 .single-journal ul li {
		margin: 0 1rem;
	}

	#about-pic {
		max-width: 200px;
		border-radius: 5px;
		display: block;
		margin: auto;
	}

	@media screen and (max-width: 680px) {
	.single-journal	.title {
			font-size: 3rem;
		}

		.single-journal {
			padding: 0 1rem;
		}
}

</style>
