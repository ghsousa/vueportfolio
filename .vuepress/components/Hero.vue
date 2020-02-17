<template>
<div class="hero-div">
	<img class="profile-pic" src="/upload/gabe.jpg">
  <h1 v-if="text" class="title" v-html="text" />
	<p class="hero-paragraph"> These bespectacled eyes see things. These trap-beat loving ears hear things. This Brazilian born, Bay State raised soul feels things - and I turn it all into immersive digital art. </p>
</div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: false
    }
  }
}
</script>

<style scoped>

	.hero-div {
		margin-bottom: 3rem;
	}

  .title {
    text-align: center;
    font-weight: 300;
		font-family: 'Avenir Next';
		font-weight: 600;
		letter-spacing: -3px !important;
    line-height: 1.25;
    letter-spacing: 0.1rem;
    width: 800px;
    max-width: 100%;
    margin: 0 auto 1vw auto;
  }

	.hero-paragraph {
		max-width: 680px;
		text-align: center;
		margin-bottom: 2rem;
		font-size: 1.2rem;
		font-weight: 400;
		max-width: 35rem;
	}

	.profile-pic {
		display: block;
		margin: auto;
		max-width: 120px;
		border-radius: 100%;
	}

  @media screen and (min-width: 600px) {
    .title {
      margin: 0 auto 1vw auto;
    }
  }

</style>
