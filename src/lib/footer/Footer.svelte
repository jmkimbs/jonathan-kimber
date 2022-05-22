<script lang="ts">
	import mail_logo from './mail.ico';
	import github_logo from './github.png';
	import linkedin_logo from './linkedin.png';
</script>

<footer>
	<a href='mailto:jonathan@jonathankimber.com'><img class='ma' src={mail_logo} alt='Send me an email' /></a>
	<a href='https://github.com/jmkimbs'><img class='gh' src={github_logo} alt='Check out my GitHub' /></a>
	<a href='https://www.linkedin.com/in/jonathan-kimber/'><img class='lin' src={linkedin_logo} alt='Check me out on LinkedIn' /></a>
</footer>

<style>

	footer {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		padding: 0px;
		background: rgba(255, 255, 255, 0.8);
		width: 100%;
	}

	img {
		padding: 0.5em 1em 0.5em 1em;
	}

	.ma {
		width: 32px;
		height: 32px;
	}

	.gh {
		width: 32px;
		height: 32px;
	}

	.lin {
		width: 32px;
		height: 27px;
	}

	p {
		margin: 0;
	}
</style>