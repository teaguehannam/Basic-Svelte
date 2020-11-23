<script>
	import Nav from './Nav.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	let players = [
		{
			name: "Spider Man",
			points: 545
		},
		{
			name: "Iron Man",
			points: 69420
		},
		{
			name: "Bat Man",
			points: 1002
		}
	];

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	}

	const removePlayer = (e) => {
		players = players.filter(player => player.name !== e.detail);
	}

</script>

<Nav />
<div class="conatiner">
	<AddPlayer on:addplayer={addPlayer} />
	{#if players.length === 0}
		<p>No Players</p>
	{:else}
		{#each players as player}
			<Player 
				name={player.name} 
				points={player.points} 
				on:deleteplayer={removePlayer}
			/>
		{/each}
	{/if}

</div>

