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
	export let blogPostId: number;
	export let blogPost: any;

	// import blogPost from `$lib/blog-posts/post-${blogPostId}`;

	// const postPath:string = `$lib/blog-posts/post-${postId}.json`

	// import blogPosts from '$lib/blog-posts';
	// const blogPost = require(blogPosts + `${postId}`);
</script>
<h1>
	{blogPost.title.S}
</h1>

{#each blogPost.body.SS as postComponent}
	{@html postComponent}
{/each}

<!-- {blogPost} -->

<!-- {postPath} -->

{blogPostId}

<!-- {@html blogPostData} -->

<style>

</style>