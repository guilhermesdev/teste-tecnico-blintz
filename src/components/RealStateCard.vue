<template>
	<div class="card">
		<div class="content-wrapper">
			<div class="image-wrapper">
				<img
					:src="data.image"
					alt="real state photo"
				/>
			</div>
			<div class="info">
				<div class="text">
					<h2>{{ data.address }}</h2>
					<span class="block mt-1">
						{{ data.city }}, {{ data.state }}, {{ data.zip }}
					</span>
				</div>
				<div class="button-group">
					<button class="success mr-2">SHARE</button>
					<button class="outline">ARCHIVE</button>
				</div>
			</div>
		</div>

		<div class="circle mr-6">
			RS
		</div>
	</div>
</template>

<script>
export default {
	name: 'RealStateCard',
	props: {
		data: {
			type: Object,
			required: true
		}
	}
}
</script>

<style lang="scss" scoped>
.card {
	display: flex;
  justify-content: space-between;
  align-items: center;

  background-color: var(--color-bg);
	color: var(--color-text);

  border-radius: .3rem;
  border: 2px solid var(--color-border);

	&:not(:last-child) {
		margin-bottom: .7rem;
	}

	@media (max-width: 630px) {
		.circle {
			display: none;
		}
	}
}

.content-wrapper {
	display: flex;

	@media (max-width: 500px) {
		width: 100%;
		flex-direction: column;
	}
}

.image-wrapper {
	height: 180px;
	width: 180px;

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	@media (max-width: 500px) {
		width: 100%;
	}
}

.info {
	display: flex;
	flex-direction: column;
	align-items: flex-start;
	justify-content: space-evenly;
	padding-top: .5rem;
	margin-left: 1rem;

	@media (max-width: 500px) {
		padding: 1rem;
		margin-left: 0;

		.button-group > * {
			flex: 1;
			margin-top: 1.5rem;
		}
	}

	h2 {
		font-size: 2rem;
	}

	.text span {
		font-size: 1.2rem;
	}

	.button-group {
		display: flex;
		width: 100%;
	}
}

button {
	padding: .6rem 1.3rem;
	font-size: 1rem;
	font-weight: 600;
	border: 0;
	border-radius: 5px;

	display: inline-flex;
  justify-content: center;
  align-items: center;

	cursor: pointer;
	transition: .3s;

	border: 2px solid transparent;

	&:hover {
		filter: brightness(.9);
	}

	&.success {
		background-color: #5db253;
		color: #fff;
	}

	&.outline {
		border-color: #435983;
		color: #435983;
	}
}

.circle {
	background-color: #eee;
	color: #fff;
	border-radius: 50%;
	font-size: 2rem;
	text-transform: uppercase;
	padding: 1rem;
}

</style>