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
	width: 50%;
  margin: auto;
	position: absolute;
	bottom: 50%;
	left:50%;
	transform: translate(-50%, 50%);
}



/* Fading animation */
.fade {
  -webkit-animation-name: fade;
  -webkit-animation-duration: 1s;
  animation-name: fade;
  animation-duration: 1s;
}

@-webkit-keyframes fade {
   0% {transform: scale(.8); opacity: 0;}
	75% {opacity: 1;}
  100% {transform: scale(1);}
}

@keyframes fade {
  0% {transform: scale(.8); opacity: 0;}
	75% {opacity: 1;}
  100% {transform: scale(1);}
}
</style>