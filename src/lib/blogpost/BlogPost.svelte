<script lang="ts">
	export let pageTitle: string;
	export let metaDescription: string;
	export let blogPostTitle: string;
	export let blogPostBody: string;
	export let blogPostEditDates: any;
</script>

<!-- {console.log(blogPostEditDates)} -->

<svelte:head>
	<title>{ pageTitle }</title>
	<meta name='description' content={metaDescription} />
</svelte:head>

<div class='blogpost'>


	<h1>
		{ blogPostTitle }
	</h1>
	
	{ @html blogPostBody }


	{#if blogPostEditDates.length >= 1}
		<h3>
			{ 'First posted: ' + new Date(blogPostEditDates[0]).toLocaleString() }
		</h3>
	{/if}

	{#if blogPostEditDates.length > 1}
		<h3>
			{ 'Last edited: ' + new Date(blogPostEditDates[blogPostEditDates.length - 1]).toLocaleString() }
		</h3>
	{/if}
	
</div>


<style>

	.blogpost :global(h1) {
		font-size: 3em;
		font-family: Garamond;
		margin-bottom: 0px;
	}

	.blogpost :global(h2) {
		font-family: Garamond;
		font-size: 2em;
	}

	.blogpost :global(h3) {
		font-family: Garamond;
		margin-top: 0px;
		margin-bottom: 0px;
		font-size: 0.85em;
	}

	.blogpost :global(p) {
		font-family: Garamond;
		text-align: justify;
		font-size: 1em;
		margin-bottom: 0.25em;
	}

	.blogpost :global(p:last-of-type) {
		margin-bottom: 5em;
	}

</style>