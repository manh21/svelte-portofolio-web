<script>
	import Navbar from "./Navbar.svelte";
	import Projects from "./Projects.svelte";
	export let name;
</script>

<Navbar/>
<main>
	<h1>{name}</h1>
	<p>Kumpulan project - project web dev</p>
</main>
<Projects/>
<div class="h-1/5"></div>

<style global lang="postcss">
	/* only apply purgecss on utilities, per Tailwind docs */
	/* purgecss start ignore */
	@tailwind base;
	@tailwind components;
	/* purgecss end ignore */
	@tailwind utilities;

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>