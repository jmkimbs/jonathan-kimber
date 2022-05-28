<script context='module' lang='ts'>

	export async function load({ params, fetch  }) {

		const blogPostId: number = params.id;

		let fetchBlogPost = await fetch('https://7h6tj6m373.execute-api.us-east-1.amazonaws.com/blog/posts')
							.then((response) => response.text())
							.then((response) => JSON.parse(response));

		return {
			props: {
				blogPostId,
				blogPost: fetchBlogPost,
			},
		};
	};
</script>

<script lang='ts'>

	import MarkdownIt from 'markdown-it';
	const md = new MarkdownIt();

	export let blogPostId: number;
	export let blogPost: any;
	
</script>

{#await blogPost}
	<h1>Loading...</h1>
	<p>I'd say grab a coffee or nip to the loo quickly but... the blog post should be here very soon.</p>
{:then blogPostResult}
	{@const thisBlogPost = blogPostResult.Items[0]}

	<h1>
		{thisBlogPost.title.S}
	</h1>
	{@html md.render(thisBlogPost.body.S) }

{:catch error}
	<p>{error.message}</p>
{/await}

<style>

</style>