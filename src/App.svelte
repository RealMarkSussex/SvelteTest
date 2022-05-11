<script>
  import { onMount } from "svelte";

  let count = 0;

  function addOne() {
    count += 1;
  }

  let searchResults = [];

  onMount(async () => {
		const res = await fetch(`https://en.wikipedia.org/w/api.php?action=opensearch&format=json&search=bob&origin=*`);
		searchResults = (await res.json())[1];
	});
</script>

<button on:click={addOne}>Clicked {count} times</button>

<ul>

	{#each searchResults as names}
		<li>{names}</li>
	{:else}
		<p>loading...</p>
	{/each}
</ul>

<style>
  /* styles go here */
</style>
