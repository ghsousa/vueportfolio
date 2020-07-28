<template>
	<div class="hero-div">
				<h1 v-if="text" class="title" v-html="text" />
				<router-link to="/about/">
				<a id="hero-paragraph">hello<span id="hero-span">.</span></a>
				</router-link>
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
				window.sessionStorage.setItem('animated', 1);
			}
	}
}
</script>
<style scoped>

.hero-div {

		height: 100vh;

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
	position: absolute;
	bottom: 50%;
	left:50%;
	transform: translate(-50%, 50%);
	margin-bottom: 0;
	margin-left: 0;
	font-weight: 300;
	color: transparent;
	font-family: Canela;
	font-size: 30vw;
  transition: all 500ms cubic-bezier(0.25, 0.8, 0.25, 1);
	-webkit-text-stroke: 2px #000;
}

#hero-paragraph:hover {
	color: #000;
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
	color: #fff;
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

		opacity: 0;
	}

	50% {
		opacity: 0;
	}

	100% {

		opacity: 1;
	}
}

/* @media (prefers-color-scheme: dark) {
	.hero-div {
	background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)),
	url("/upload/gabe-night.jpg");
	background-size: cover;
	background-position: 50%;
	justify-content: flex-end;
}
#hero-paragraph {
	color: #fff;
		-webkit-text-stroke: 2px #fff;
}
} */

</style>
