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


	.blogpost :global(h2) {
		color: green;
	}

	:global(h2) {
		color: red;
	}

</style>