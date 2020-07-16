<template>
	<div class="hero-div">
		<div class="grid">
			<div class="grid-item" id="bio">
				<h1 v-if="text" class="title" v-html="text" />
				<router-link to="/about/">
				<a id="hero-paragraph">hello<span id="hero-span">.</span></a>
				</router-link>
			</div>
			<div class="grid-item" id="menu">
				<router-link to="/art/"><h1 id="art">Art</h1></router-link>
				<router-link to="/journal/"><h1 id="journal">Journal</h1></router-link>
				<a href="https://twitter.com/gabedotcss" target="_blank">	<h1  id="twitter">Twitter</h1></a>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		text: {
			type: String,
			required: false
		}
	},
	mounted () {
			if (window.sessionStorage.getItem('animated') === null) {
				document.getElementById("hero-paragraph").classList.add('animate');
				document.getElementById("art").classList.add('animate_art');
				document.getElementById("journal").classList.add('animate_journal');
				document.getElementById("twitter").classList.add('animate_twitter');
				window.sessionStorage.setItem('animated', 1);
			} else {
				document.getElementById("art").style.opacity = 1;
				document.getElementById("journal").style.opacity = 1;
					document.getElementById("twitter").style.opacity = 1;
			}
	}
}
</script>
<style scoped>.grid {
	display: grid;
	grid-template-columns: 1fr 1fr;
	height: 100vh;
	background-color: #fff;
}

.grid h1 {
	font-family: Canela;
}


.grid-item {
	display: flex;
	place-items: center;
	flex-direction: column;
	justify-content: center;
}

.title {
	text-align: center;
	font-weight: 300;
	font-weight: 600;
	letter-spacing: -3px !important;
	line-height: 1.25;
	letter-spacing: 0.1rem;
	width: 800px;
	max-width: 100%;
	margin: 0 auto 1vw auto;
}

#hero-paragraph {
	margin-bottom: 0;
	margin-left: 0;
	font-weight: 300;
	color: #fff;
	font-family: Canela;
	font-size: 20vw;
	left: 0;
  transition: all 500ms cubic-bezier(0.25, 0.8, 0.25, 1);
		-webkit-text-stroke: 2px #fff;
}

#hero-paragraph:hover {
	color: transparent;
}

#hero-span {
	margin: -10px;
}

.animate {
	animation: 1s ease-out 0s 1 slideInFromLeft;
	animation-iteration-count: 1;
}

.animate_art {
	animation: 1s ease-out .1s 1 slideInFromBottom;
	animation-fill-mode: forwards;
}

.animate_journal {
	animation: 1s ease-out .2s 1 slideInFromBottom;
	animation-fill-mode: forwards;
}

.animate_twitter {
	animation: 1s ease-out .3s 1 slideInFromBottom;
	animation-fill-mode: forwards;
}

#bio {
	/* background: linear-gradient(#222, #111) */
	background: url("/upload/gabe.jpg");
	background-size: cover;
	background-position: center;
	justify-content: flex-end;
}

h1:hover {
	text-decoration: underline;
}

#projects,
#art,
#journal,
#twitter {
	font-size: 4rem;
	padding: 1rem 2rem;
	transition: all 750ms cubic-bezier(0.25, 0.8, 0.25, 1);
	opacity: 0;
	margin: 2rem auto;
}


@media screen and (min-width: 600px) {
	.title {
		margin: 0 auto 1vw auto;
	}
}

@media screen and (max-width: 680px) {
	.grid {
		grid-template-columns: 1fr;
	}

	#bio {
		order: 2;
		background-size: cover;
		background-position: center -90px;
	}

	#hero-span {
		margin: -10px;
	}


	#projects,
	#art,
	#journal,
	#twitter {
		font-size: 3rem;
		margin-bottom: 1rem;
	}
}

@media screen and (max-width: 1000px) {
	.hero-paragraph {
		font-size: 13vw;
	}
}

@keyframes headline {
	from {
		color: #fff;
	}

	to {
		color: #000;
	}
}

@keyframes slideInFromBottom {
	0% {
		transform: translateY(100%);
		opacity: 0;
	}

	50% {
		opacity: 0;
	}

	100% {
		transform: translateY(0);
		opacity: 1;
	}
}

@keyframes slideInFromLeft {
	0% {
		transform: translateX(-100%);
		opacity: 0;
	}

	50% {
		opacity: 0;
	}

	100% {
		transform: translateX(0);
		opacity: 1;
	}
}

</style>
