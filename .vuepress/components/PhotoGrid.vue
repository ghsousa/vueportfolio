<template>
	<div class="container grid">
	
		<div class="grid-image" style="background:url('/upload/photos/DSC00191.jpg')">
		</div>

		<div class="grid-image" style="background:url('/upload/photos/_DSC0123.jpg')">
		</div>

		<div class="grid-image" style="background:url('/upload/photos/57446015-A6E2-40FC-A876-22153B612C20.jpg')">
		</div>


	</div>
</template>

<style scoped>

.grid {
	display: grid;
	position: relative;
	grid-template-columns: 1fr;
}

.grid-image {
	background-size: cover !important;
	background-attachment: fixed !important;
	height: 100vh;
}

	.grid .grid-image {
		display: flex;
		align-items: center;
	}

	@media screen and (max-width: 728px) { 
		.grid-image { 
			background-position: center;
			background-size:contain;
		 }

	}


</style>
