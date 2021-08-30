<script>
  import StoryCard from "./StoryCard.svelte"
	export let data
</script>

{#each data as doc, i}
  <StoryCard doc={doc} />
{/each}
