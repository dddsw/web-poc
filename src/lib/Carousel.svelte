<script lang="ts">
	let carouselImages = [
		{ id: 1, src: '../images/carousel/carousel-1.jpg' },
		{ id: 2, src: '../images/carousel/carousel-2.jpg' },
		{ id: 3, src: '../images/carousel/carousel-3.jpg' },
		{ id: 4, src: '../images/carousel/carousel-4.png' },
		{ id: 5, src: '../images/carousel/carousel-5.png' },
		{ id: 6, src: '../images/carousel/carousel-6.jpg' }
	];

	$: carouselImage = carouselImages[0];

	setInterval(() => {
		const currentId = carouselImage.id;
		if (currentId === carouselImages.length) {
			carouselImage = carouselImages[0];
		} else {
			carouselImage = carouselImages[currentId];
		}
	}, 5000);
</script>

{#key carouselImage}
	<div class="header" style="background-image: url({carouselImage.src});">
		<slot />
		<div class="details-container shadow">
			<span class="name">DDD South West</span><br />
			<span class="details">29th April 2023 @ Engine Shed</span>
		</div>
	</div>
{/key}

<style>
	.header {
		background-size: cover;
		background-position: center;
		min-height: 250px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.details-container {
		color: white;
		margin-left: 30px;
		margin-bottom: 10px;
	}

	.name {
		font-size: 1.5rem;
		font-weight: bold;
	}

	.shadow {
		box-shadow: 0px 0px 50px 43px rgb(0 0 0 / 50%);
		background-color: rgb(0 0 0 / 50%);
	}

	@media (min-width: 350px) {
		.name {
			font-size: 2rem;
		}
	}

	@media (min-width: 768px) {
		.name {
			font-size: 3rem;
		}

		.details {
			font-size: 1.5rem;
		}

		.details-container {
			margin-left: 100px;
			margin-bottom: 50px;
		}

		.header {
			min-height: 400px;
		}
	}

	@media (min-width: 992px) {
		.name {
			font-size: 5rem;
		}

		.details {
			font-size: 2rem;
		}
	}

	@media (min-width: 1200px) {
		.header {
			min-height: 500px;
		}
	}

	@media (min-width: 1800px) {
		.header {
			min-height: 700px;
		}

		.details-container {
			margin-left: 25%;
		}
	}
</style>
