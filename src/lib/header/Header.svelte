<script lang="ts">
	import { page } from '$app/stores';
	import logo from './svelte-logo.svg';
</script>

<header>
	<div class='corner'>
		<a href='https://kit.svelte.dev'>
			<img src={logo} alt='SvelteKit' />
		</a>
	</div>

	<nav>
		<ul>
			<li class:active={$page.url.pathname === '/'}>
				<a sveltekit:prefetch href='/'>about me</a>
			</li>
			<li>
				<span class='spacer'>\</span>
			</li>
			<li class:active={$page.url.pathname === '/blog'}>
				<a sveltekit:prefetch href="/blog">blog</a>
			</li>
			<li>
				<span class='spacer'>/</span>
			</li>
			<li class:active={$page.url.pathname === '/projects'}>
				<a sveltekit:prefetch href="/projects">projects</a>
			</li>
			<li>
				<span class='spacer'>\</span>
			</li>
			<li class:active={$page.url.pathname === '/project-works'}>
				<a sveltekit:prefetch href="/project-works">project works</a>
			</li>
		</ul>
	</nav>

	<div class='corner'>
		<!-- TODO put something else here? github link? -->
	</div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		background: rgba(255, 255, 255, 0.85);
	}

	.corner {
		width: 3em;
		height: 3em;
		opacity: 0;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}

	nav {
		display: flex;
		justify-content: center;
	}

	svg {
		width: 2em;
		height: 3em;
		display: block;
	}

	path {
		fill: var(--background);
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	li.active::before {
		--size: 6px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: 0;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid var(--accent-color);
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		text-align: center;
		padding: 0 1em 0 1em;
		color: var(--heading-color);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	nav a:hover {
		color: var(--accent-color);
	}

	nav .spacer {
		display: flex;
		height: 100%;
		align-items: center;
		/* padding: 0 1em; */
		color: var(--heading-color);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
	}

	@media (min-width: 480px) {
		nav .spacer {
			/* padding: 0 0.5em 0 0.5em; */
		}

		nav a {
			/* padding: 0 0.5em 0 0.5em; */
		}
	}

	@media (min-width: 540px) {
		nav a {
			padding: 0 1.5em 0 1.5em;
		}
	}

	@media (min-width: 600px) {
		nav a {
			padding: 0 2em 0 2em;
		}
	}

	@media (min-width: 720px) {
		nav a {
			padding: 0 2.5em 0 2.5em;
		}

		.corner {
			opacity: 1;
		}
	}

	@media (min-width: 840px) {
		nav a {
			padding: 0 3em 0 3em;
		}
	}

	@media (min-width: 960px) {
		nav a {
			padding: 0 3.5em 0 3.5em;
		}
	}

	@media (min-width: 1080px) {
		nav a {
			padding: 0 4em 0 4em;
		}
	}

	@media (min-width: 1200px) {
		nav a {
			padding: 0 4.5em 0 4.5em;
		}
	}

	@media (min-width: 1320px) {
		nav a {
			padding: 0 5em 0 5em;
		}
	}

	@media (min-width: 1440px) {
		nav a {
			padding: 0 5.5em 0 5.5em;
		}
	}

	@media (min-width: 1560px) {
		nav a {
			padding: 0 6em 0 6em;
		}
	}
</style>
