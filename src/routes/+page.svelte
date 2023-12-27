<script lang="ts">
	export const prerender = true;

	import PlayerContainer from '$lib/PlayerContainer.svelte';

	export type PowerUps = {
		[key: 'shield' | 'choose' | 'double']: number;
	};

	export type Player = 'green' | 'red' | 'blue' | 'yellow';

	type Game = {
		[key in Player]: PowerUps;
	};

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
	};

	let game = JSON.parse(JSON.stringify(DEFAULT_GAME)) as Game;

	const updateGame = (player: Player, powerUp: keyof PowerUps, value: number) => {
		if (value < 0) {
			value = 0;
		}

		game = {
			...game,
			[player]: {
				...game[player],
				[powerUp]: value
			}
		};
	};

	const players = ['green', 'red', 'blue', 'yellow'];
</script>

<main>
	<h1>Ludo World Tracker</h1>
	<p>
		A companion app for <a href="https://www.facebook.com/RealLudoSuperstar/" target="_blank"
			>Ludo World</a
		> to help you keep track of your and your opponents powerups.
	</p>
	<section>
		{#each players as player}
			<PlayerContainer playerColor={player} {game} {updateGame} />
		{/each}
	</section>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600&display=swap');
	:global(body) {

		font-family: 'Barlow Condensed', sans-serif;
	}

	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		color: white;
		max-width: calc(100vw - 2rem);
		margin: 0 auto;
	}

	a {
		color: white;
	}

	h1 {
		font-size: 2rem;
		text-align: center;
		margin-bottom: 1rem;
	}

	p {
		margin-top: 0;
		font-size: 1.5rem;
		text-align: center;
	}

	section {
		width: 100%;
	}
</style>