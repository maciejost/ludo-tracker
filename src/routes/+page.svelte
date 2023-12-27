

<script lang="ts">
	export const prerender = true

	import PlayerContainer from '$lib/PlayerContainer.svelte'

	export type PowerUps = {
	[key: 'shield' | 'choose' | 'double'] : number
	}

	export type Player = 'green' | 'red' | 'blue' | 'yellow'

	type Game = {
		[key in Player]: PowerUps
	}

	const DEFAULT_GAME = {
		green: {
			shield: 0,
			choose: 0,
			double: 0
		},
		red: {
			shield: 0,
			choose: 0,
			double: 0
		},
		blue: {
			shield: 0,
			choose: 0,
			double: 0
		},
		yellow: {
			shield: 0,
			choose: 0,
			double: 0
		}
	}

	let game = JSON.parse(JSON.stringify(DEFAULT_GAME)) as Game

	const updateGame = (player: Player, powerUp: keyof PowerUps, value: number) => {

		if (value < 0) {
			value = 0
		}

		game = {
			...game,
			[player]: {
				...game[player],
				[powerUp]: value
			}
		}

		console.log('game', game)
	}

	const players = ['green', 'red', 'blue', 'yellow']

</script>
<main>
	<h1>Ludo World Tracker</h1>
	<p>A companion app for <a href="https://www.facebook.com/RealLudoSuperstar/" target="_blank">Ludo World</a> to help you keep track of your opponents powerups.</p>
	{#each players as player}
		<PlayerContainer playerColor={player} {game} {updateGame} />
	{/each}
</main>