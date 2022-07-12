<script>
	export let segment;
</script>

<style>
 
	nav {
		border-bottom: 1px solid rgba(255,62,0,0.1);
		font-weight: 400;
		padding: 0 1em;
		background-color: rgba(161, 196, 253);
		font-family: 'Oranienbaum, Poppins, Roboto';
		transition: 1s;	
	}

	nav:hover{
		background-color: rgb(101, 158, 248);
		transition: 0.7s;
	}

	nav:hover a{
		color: white;
		transition: 0.7s;
	}

	ul {
		margin: 0;
		padding: 0 ;

		display: flex;
		justify-content: center;
		align-items: center;
	}

	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		display: block;
		padding: 0 40px;
		font-size: 20px;
	}

	[aria-current] {
		position: relative;
		display: inline-block;
	}

	[aria-current]::after {
		position: absolute;
		content: '';
		width: calc(100% - 1em);
		height: 2px;
		background-color: rgb(255,62,0);
		display: block;
		bottom: -1px;
	}

	a {
		text-decoration: none;
		padding: 1em 0.5em;
		display: block;
		transition: 1s;

	}

</style>

<nav>
	<ul>
		<li id="lili"><a aria-current='{segment === undefined ? "page" : undefined}' href='.'><b>Home</b></a></li>
		<li><a onclick="change" aria-current='{segment === "stats" ? "page" : undefined}' href='stats'><b>Stats</b></a></li>
        <li><a aria-current='{segment === "players" ? "page" : undefined}' href='players'><b>Players</b></a></li>
	</ul>
</nav>
