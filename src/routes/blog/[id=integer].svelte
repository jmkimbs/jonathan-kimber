<script context='module' lang='ts'>

	export async function load({ params }) {
		const blogPostId: number = params.id;

		const blogPost: any = await import(`./../../lib/blog-posts/post-${blogPostId}`);

		return {
			props: {
				blogPostId,
				blogPost,
			},
		};
	};
</script>

<script lang='ts'>
	// var md = import('markdown-it')();

	import { parse } from "cookie";
	import { text } from "svelte/internal";

	import MarkdownIt from 'markdown-it';
	const md = new MarkdownIt();

	// let md = window.markdownit();

	export let blogPostId: number;
	export let blogPost: any;
	// const result: string = md.render('# markdown-it rulezz!');

	let blogPostJson: any;

	let fetchBlogPost = fetch('https://7h6tj6m373.execute-api.us-east-1.amazonaws.com/blog/posts')
							.then((response) => response.text())
							.then((response) => JSON.parse(response));

	
</script>

{blogPostId}

<h1>
	{blogPost.title.S}
</h1>

{#each blogPost.body.SS as postComponent}
	{@html postComponent}
{/each}

{#await fetchBlogPost}
	<p>No blog post yet...</p>
{:then blogPostResult}
	<!-- {console.log(blogPostResult)} -->
	<p>Below me should be a stringified blog post</p>
	<pre>{JSON.stringify(blogPostResult.Items, undefined, 2)}</pre>
	<!-- <p>{blogPostResult}</p> -->

	{@html md.render(blogPostResult.Items[0].body.S) }

	The end

	<!-- {console.log(blogPostResult)}; -->
<!-- {:then bpr} -->
	<!-- console.log(bpr); -->
{:catch error}
	<p>{error.message}</p>
{/await}


<!-- {@html blogPostData} -->

<style>

</style>