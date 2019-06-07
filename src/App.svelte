<script>
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';
	let foo = `this string contains some <strong>HTML!!!</strong>`;

	let players = [
		{
			name: "John Doe",
			points: 43
		},
		{
			name: "Sam Smith",
			points: 45
		},
		{
			name: "Sara Wilson",
			points: 33
		}
	];

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	};

	const removePlayer = (e) => {
		players = players.filter(player => player.name !== e.detail);
	}
</script>

<Navbar />

<div class="container">

	<p>{@html foo}</p>

	<AddPlayer on:addplayer={addPlayer} />

	{#if players.length === 0}
	<p>No Player</p>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.points} 
			on:removeplayer={removePlayer} />
		{/each}
	{/if}
</div>
