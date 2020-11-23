<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	
	export let name;
	export let points;
	let showControls = false;

	const addPoint = () => points += 1;
	const removePoint = () => points -= 1;
	const toggleControls = () => showControls = !showControls;
	const handleDelete = () => dispatch("deleteplayer", name);

</script>

<style>
	h1 {
		color: grey;
	}
</style>

<div class="card">
	<h1>{name}</h1>

	<button class="toggleControls" on:click={toggleControls}>
		{#if showControls}Hide Controls{:else}Show Controls{/if}
	</button>
	<button class="delete" on:click={handleDelete}>x</button>

	<h3>You have {points} points!</h3>
	{#if showControls}
		<button on:click={addPoint}>+1</button>
		<button on:click={removePoint}>-1</button>
		<br>
		<input type="number" bind:value={points} />
	{/if}
</div>

