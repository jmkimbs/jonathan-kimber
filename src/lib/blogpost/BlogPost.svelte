<script lang="ts">
	export let pageTitle: string;
	export let metaDescription: string;
	export let blogPostTitle: string;
	export let blogPostBody: string;
</script>

<svelte:head>
	<title>{ pageTitle }</title>
	<meta name='description' content={metaDescription} />
</svelte:head>

<div class='blogpost'>

	<h1>
		{ blogPostTitle }
	</h1>
	
	{ @html blogPostBody }
	
</div>


<style>

	.blogpost :global(h1) {
		font-size: 3em;
		margin-bottom: 0px;
	}

	.blogpost :global(h2) {
		margin-top: 1.5em;
		font-size: 2em;
	}

	.blogpost :global(p) {
		text-align: justify;
		margin-bottom: 0.25em;
	}

	.blogpost :global(p:last-child) {
		margin-bottom: 7em;
	}

</style>