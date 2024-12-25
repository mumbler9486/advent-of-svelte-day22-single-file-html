<script>
	import '../app.css';
</script>

<div class="page">
	<h1>2025 Fortunes</h1>

	<a class="button" href="#/fortune">Get your new years Fortune</a>
	<a class="button" href="https://github.com/mumbler9486/advent-of-svelte-day22-single-file-html">GitHub (see day 22 page)</a>
</div>


<style scoped>
	h1{
		color: white;
	}
	.page {
		display: flex;
		border-radius: 1rem;
		background-color: #2D308E;
		padding: 2rem;
		flex-direction: column;
	}
	.button {
		margin-top: 1rem;
		padding: 1rem;
		border-width: 1px;
		border-radius: 0.5rem;
		background-color: purple;
		font-weight: 600;
		font-size: 0.875rem;
		text-decoration: none;
		color: white;
		text-align: center;
	}
</style>