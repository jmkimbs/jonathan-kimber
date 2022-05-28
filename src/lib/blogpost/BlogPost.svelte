<script lang="ts">
	export let pageTitle: String;
	export let metaDescription: String;
	export let blogPostTitle: String;
	export let blogPostBody: String;
</script>

<svelte:head>
	<title>{ pageTitle }</title>
	<!-- <meta name="description" content={metaDescription} /> -->
</svelte:head>

<div class='blogpost'>
	<h1>
		{ blogPostTitle }
	</h1>
	
	{ @html blogPostBody }
	
	{ @html '<h2>Test</h2>'}
	<h2>Test2</h2>
</div>


<style>


	.blogpost :global(h2) {
		color: green;
	}

	:global(h2) {
		color: red;
	}

</style>