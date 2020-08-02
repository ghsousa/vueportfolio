<template>

<div class="slideshow-container">
  <!-- Full-width images with number and caption text -->
	 <div class="mySlides fade">
    <img src="/upload/boat.jpeg" style="width:100%">
  </div>

  <div class="mySlides fade">
    <img src="/upload/IMG_0093.png" style="width:100%">
  </div>

	 <div class="mySlides fade">
    <img src="/upload/three-plants.png" style="width:100%">
  </div>

</div>

</template>

<script>
export default {
	mounted: function(){
			var slideIndex = 1;
			showSlides(slideIndex);

			// Next/previous controls
			function plusSlides(n) {
				showSlides(slideIndex += n);
			}

			// Thumbnail image controls
			function currentSlide(n) {
				showSlides(slideIndex = n);
			}

			var slideIndex = 0;
showSlides();

function showSlides() {
  var i;
  var slides = document.getElementsByClassName("mySlides");
  for (i = 0; i < slides.length; i++) {
    slides[i].style.display = "none";
  }
  slideIndex++;
  if (slideIndex > slides.length) {slideIndex = 1}
  slides[slideIndex-1].style.display = "block";
  setTimeout(showSlides, 5000);
}
		}
	}
</script>

<style scoped>

/* Slideshow container */
.slideshow-container {
	max-width: 800px;
<<<<<<< HEAD
	width: 50%;
  margin: auto;
	position: absolute;
	bottom: 50%;
	left:50%;
	transform: translate(-50%, 50%);
=======
	width: 95%;
    margin: auto;
    margin-top: 15vh;
>>>>>>> 72c1a3f30dd8c9508fbb7bf969511c0694c8e4f7
}

</style>