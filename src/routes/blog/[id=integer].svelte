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
	import Error from '$lib/error/Error.svelte'
	import MarkdownIt from 'markdown-it';
	const md = new MarkdownIt();

	export let blogPostId: number;
	export let blogPost: any;
	
</script>

{#await blogPost}

	<BlogPost
		pageTitle={String('Blog post #' + blogPostId)}
		metaDescription={String('Placeholder description')}
		blogPostTitle={String('Loading...')}
		blogPostBody={String("<p>I'd say grab a coffee or nip to the loo quickly but... the blog post should be here very soon.</p>")}
	/>

{:then blogPostResult}

	{ @const thisBlogPost = blogPostResult.Items[0] }
	{ @const pageTitle = String('Blog - ' + thisBlogPost.title.S) }
	{ @const blogPostTitle = String(thisBlogPost.title.S)}
	{ @const blogPostBody = String(md.render(thisBlogPost.body.S)) }
	
	<BlogPost 
		pageTitle={pageTitle}
		metaDescription='TODO: description logic (manually written or body trimmed or ?)'
		blogPostTitle={blogPostTitle}
		blogPostBody={blogPostBody}
	/>

{:catch error}

	<Error
		errorTitle={String('Error')}
		errorPicture={String('$static/svelte-welcome.png')}
		errorBody={String(error.message)}
	/>

{/await}
