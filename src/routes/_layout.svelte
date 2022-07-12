<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	main {
		position: relative;
		max-width: 100%;
		background-color: white;
		background-image: linear-gradient(to top, rgb(201, 196, 196), rgb(255, 255, 255));
		box-shadow: 0px 0px 9px gray;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
		
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>