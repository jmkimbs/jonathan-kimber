<script context='module' lang='ts'>

	/** @type {import('@sveltejs/kit').Load} */
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
	import BlogPost from '$lib/blogpost/BlogPost.svelte'
	import MarkdownIt from 'markdown-it';
	const md = new MarkdownIt();

	export let blogPostId: number;
	export let blogPost: any;
	
</script>

<svelte:head>
	<!-- {#await blogPost}
		<title>Blog post #{blogPostId}</title>
	{:then blogPostResult}
		<title>Blog - {blogPostResult.Items[0].title.S}</title>
	{/await} -->

</svelte:head>

{#await blogPost}
	<BlogPost
		pageTitle='Blog post #{blogPostId}'
		metaDescription='Placeholder description'
		blogPostTitle='Loading...'
		blogPostBody="<p>I'd say grab a coffee or nip to the loo quickly but... the blog post should be here very soon.</p>"
	/>
	
{:then blogPostResult}


	{ @const thisBlogPost = blogPostResult.Items[0] }
	{ @const pageTitle = 'Blog - ' + thisBlogPost.title.S }
	{ @const blogPostTitle = thisBlogPost.title.S}
	{ @const blogPostBody = md.render(thisBlogPost.body.S) }
	
	<BlogPost 
		pageTitle={pageTitle}
		metaDescription='Placeholder description'
		blogPostTitle={blogPostTitle}
		blogPostBody={blogPostBody}
	/>

{:catch error}
	<p>{error.message}</p>
{/await}
