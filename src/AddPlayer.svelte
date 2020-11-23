<script>
import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

	let player = {
		name: "",
		points: 0
	}

	const handleSubmit = (e) => {
		e.preventDefault();
		dispatch("addplayer", player);
		player = { name: "", points:0 };
	}
</script>

<style>
	form {
		display: flex;
		flex-direction: column;
		max-width: 180px;
		margin: 0px auto;
		border: 1px grey solid;
		padding: 12px;
	}

	input {
		max-width: 120px;
		margin: 5px auto;
	}

	h5 {
		font-size: 1rem;
		line-height: 2rem;
		margin: 0;
	}
</style>

<form on:submit={handleSubmit}>
	<h5>Add Player</h5>
	<input type="text" placeholder="Player Name" bind:value={player.name}>
	<input type="number" placeholder="Player Points" bind:value={player.points}>
	<input type="submit" class="" value="Submit" />
</form>
