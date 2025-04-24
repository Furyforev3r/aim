<script lang="ts">
	import { goto } from "$app/navigation"
	import Icon from "@iconify/svelte"
</script>

<svelte:head>
	<title>Aim - Home</title>
	<meta name="description" content="Aim trainer" />
</svelte:head>

<div class="app">
	<section>
		<div class="container">
			<div class="title">
				<h1>Aim</h1>
				<h2>Master your aim!</h2>
			</div>
		
			<div class="content">
				<p>
					Welcome to Aim, the ultimate aim training platform! Our goal is to help you
					improve your aim and reflexes through a variety of engaging and
					challenging games. Whether you're a casual gamer or a competitive
					professional, Aim has something for everyone.
				</p>
			</div>
		</div>
	</section>

	<div class="bar"></div>

	<section>
		<div class="trainingsContainer">
			<h2>Trainings</h2>

			<div class="trainings">
				<div class="aim">
					<h3>Reflexes</h3>
					<p>
						Reflexes is a fast-paced game that tests your reaction time and
						accuracy. Click on the color as quickly as possible to get your time.
					</p>
					<button onclick={() => goto("/trainings/reflexes")}><Icon icon="mdi:play" width="24" height="24" />Play</button>
				</div>
				
				<div class="aim">
					<h3>Tracking</h3>
					<p>
						Tracking is a game designed to improve your ability to follow moving
						targets with precision. Stay focused and keep the target in your sights!
					</p>
					<button onclick={() => goto("/about")}><Icon icon="mdi:play" width="24" height="24" />Play</button>
				</div>
			</div>
		</div>
	</section>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 1rem;
		padding: 2rem;
		color: var(--text-color);
	}

	section {
		margin: 5rem;
		display: flex;
		flex-direction: column;
		width: 100%;
	}

	.container {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
		width: 100%;
	}

	.title {
		text-align: center;
	}

	h1 {
		font-size: 3rem;
		color: var(--blue-primary-color);
	}

	h2 {
		font-size: 2rem;
		color: var(--blue-secondary-color);
	}

	.content {
		max-width: 600px;
		padding: 1rem;
		background-color: var(--button-background);
		border-radius: 0.8rem;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
	}

	.content p {
		font-size: 1.2rem;
		line-height: 1.6;
	}

	.bar {
		width: 60%;
		height: 1px;
		background-color: var(--blue-primary-color);
	}

	.trainingsContainer {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1.2rem;
		width: 100%;
	}

	.trainings {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		width: 100%;
	}

	.aim {
		display: flex;
		flex-direction: column;
		align-items: start;
		justify-content: center;
		gap: 1rem;
		width: 30%;
		background-color: var(--button-background);
		padding: 1rem;
		border-radius: 0.8rem;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
	}

	button {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		gap: 1rem;
		background-color: var(--blue-primary-color);
		color: var(--button-background);
		border: none;
		width: 100%;
		padding: 1rem;
		border-radius: 0.5rem;
		cursor: pointer;
		font-weight: bold;
		font-size: 1.2rem;
		transition: background-color 0.3s ease-in-out;
	}

	button:hover {
		background-color: var(--blue-secondary-color);
	}

	@media (max-width: 768px) {
		.container {
			flex-direction: column;
			text-align: center;
			gap: 1.2rem;
		}

		.trainings {
			flex-direction: column;
			gap: 1.5rem;
		}

		.aim {
			width: 90%;
		}

		h1 {
			font-size: 2.5rem;
		}

		h2 {
			font-size: 1.8rem;
		}

		.content p {
			font-size: 1rem;
		}

		.bar {
			width: 80%;
		}
	}
</style>
