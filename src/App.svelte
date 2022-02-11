<script>
	import Nav from "./Menu.svelte"
	import Main from "./Main.svelte"
	import Footer from "./Footer.svelte"
</script>

<header>
	<Nav/>
</header>
<main>
	<Main/>
</main>
<Footer/>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>