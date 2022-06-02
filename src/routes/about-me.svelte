<script context='module' lang='ts'>

	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	export const prerender = true;

	/** @type {import('@sveltejs/kit').Load} */
	export async function load({ params, fetch  }) {

		const blogPostId: number = params.id;

		let fetchAboutMe = new Promise((resolve, reject) => {
			resolve({
				firstname: 'Jonathan',
				middlename: 'Marshall',
				surname: 'Kimber',
				age: 25,
				blurb: '',
				employmentHistory: [
					{
						company:'Amazon', 
						role: 'Software Development Engineer',
						startDate: new Date(),
						endDate: new Date(), 
						responsibilities: [
							'stuff', 
							'more stuff'
						]
					}
				],
				educationHistory: [
					{
						school:'Union College', 
						studying: 'Bachelor of Science in Computer Science', 
						startDate:'UTC-START-DATE', 
						cumulativeGrade:'3.X', 
						subjects: 
							{
								type: "Bachelor of Science", 
								subject: '', 
								grade: '3.X'
							}
					}
				],
				developmentLanguages: [
					'Java',
					'C',
					'C#',
					'C++',
					'Python',
					'JavaScript',
					'HTML',
					'CSS',
					'SQL',
					'T-SQL'
				],
				skills: [
					'Linux',
					'Git',
					'Backbone.js',
					'Qt',
					'Robot Operating System',
					'Svelte',
					'SvelteKit'
				]
			});
		});

		return {
			props: {
				aboutMe: fetchAboutMe
			},
		};
	};
</script>

<script lang='ts'>
	import ExperienceEntry from '$lib/experience/ExperienceEntry.svelte'

	export let aboutMe: any;
</script>

<svelte:head>
	<title>About me</title>
	<meta name="description" content="About this app" />
</svelte:head>

{#await aboutMe}

{:then details}

	{ @const name = details.firstname + ' ' + details.middlename + ' ' + details.surname }

	<h1>About me</h1>

	<h2>General information</h2>
	<span>{name}</span>
	<span>{details.age} years old</span>
	
	<h2>Employment history</h2>
	{#each details.employmentHistory as job}

		<ExperienceEntry 
			title={job.role}
			location={job.company}
			startDate={job.startDate}
			endDate={job.endDate}
			achievements={[]}
		/>

	{/each}

	<h2>Education history</h2>

	{#each details.educationHistory as educationItem} 
		<!-- TODO -->
	{/each}

	<h2>Skills - Languages</h2>
	<ul>
		{#each details.developmentLanguages as language}
			<li>{language}</li>
		{/each}
	</ul>

	<h2>Skills - Miscellaneous</h2>
	<ul>
		{#each details.skills as skill}
			<li>{skill}</li>
		{/each}
	</ul>
{:catch}

{/await}

<style>
	.content {
		width: 100%;
		max-width: var(--column-width);
		/* margin: var(--column-margin-top) auto 0 auto; */
	}
</style>
