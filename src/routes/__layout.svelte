<script>
	import Nav from '$lib/Nav.svelte';
</script>

<style>
	main {
		position: relative;
		background-color: white;
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}
</style>

<Nav/>

<main>
	<slot></slot>
</main>