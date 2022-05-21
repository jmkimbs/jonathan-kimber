<script lang="ts">
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
</script>

<Header />

<main>
	<slot />
</main>

<footer>
	<p>visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p>
</footer>

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 40px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 40px 0;
		}

		main {
			/* margin-left: 7%;
			margin-right: 7%; */
			width: 90%
		}
	}

	@media (min-width: 600px) {
		main {
			/* width: 80%; */
		}
	}

	@media (min-width: 720px) {
		main {
			width: 80%;
		}
	}

	@media (min-width: 840px) {
		main {
			/* width: 60%; */
		}
	}

	@media (min-width: 1080px) {
		main {
			width: 70%;
		}
	}
</style>
