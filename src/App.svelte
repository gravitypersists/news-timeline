<script>
	import data from "../data/trump-nytimes-frontpage.json"
	import Timeline from "./components/Timeline.svelte"
</script>

<main>
	<Timeline data={data} />
</main>


<style>
	main {
		margin: 0 auto;
		height: 100%;
	}
</style>
