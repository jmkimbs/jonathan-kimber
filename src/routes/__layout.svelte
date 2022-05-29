<script lang="ts">
	import Header from '$lib/header/Header.svelte';
	import Footer from '$lib/footer/Footer.svelte';
	import '../app.css';
</script>

<body>
	<Header />
	
	<main>
		<slot />
	</main>
	
	<Footer />
</body>

<style>
	body {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

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


	@media (min-width: 480px) {

		main {
			width: 90%
		}
	}

	@media (min-width: 720px) {
		main {
			width: 80%;
		}
	}

	@media (min-width: 1080px) {
		main {
			width: 70%;
		}
	}
</style>
