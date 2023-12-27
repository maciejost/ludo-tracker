<script lang="ts">
	export let playerColor: Player;
	export let game: Game;
	export let updateGame: (player: Player, powerUp: keyof PowerUps, value: number) => void;

	const background = {
		green: 'rgba(0, 255, 0, 0.1)',
		red: 'rgba(255, 0, 0, 0.1)',
		blue: 'rgba(0, 0, 255, 0.1)',
		yellow: 'rgba(255, 255, 0, 0.1)'
	};
</script>

<div class="player" style:background={background[playerColor]}>
	<h2>
		{playerColor}
	</h2>
	<div class="powerups">
		<div>
			<p class="amount">{game[playerColor].double}</p>
			<p>Double throw</p>
			<div class="buttons">
				<button on:click={() => updateGame(playerColor, 'double', game[playerColor].double + 1)}>
					+1
				</button>
				<button
					disabled={game[playerColor].double === 0}
					on:click={() => updateGame(playerColor, 'double', game[playerColor].double - 1)}
				>
					-1
				</button>
			</div>
		</div>
		<div>
			<p class="amount">{game[playerColor].choose}</p>
			<p>Choose throw</p>
			<div class="buttons">
				<button on:click={() => updateGame(playerColor, 'choose', game[playerColor].choose + 1)}>
					+1
				</button>
				<button
					disabled={game[playerColor].choose === 0}
					on:click={() => updateGame(playerColor, 'choose', game[playerColor].choose - 1)}
				>
					-1
				</button>
			</div>
		</div>
		<div>
			<p class="amount">{game[playerColor].shield}</p>
			<p>Shield</p>
			<div class="buttons">
				<button on:click={() => updateGame(playerColor, 'shield', game[playerColor].shield + 1)}>
					+1
				</button>
				<button
					disabled={game[playerColor].shield === 0}
					on:click={() => updateGame(playerColor, 'shield', game[playerColor].shield - 1)}
				>
					-1
				</button>
			</div>
		</div>
	</div>
</div>

<style>
	.player {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-bottom: 1rem;
		padding: 1rem;
		border-radius: 0.5rem;
	}
	h2 {
		margin: 0;
		margin-bottom: 0.5rem;
		text-transform: capitalize;
	}

	p:not(.amount) {
		margin: 0;
		margin-bottom: 0.5rem;
	}

	.amount {
		font-size: 2rem;
		margin: 0;
	}

	.powerups {
		text-align: center;
		display: flex;
		width: 100%;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
	}

	button {
		border: none;
		border-radius: 0.25rem;
		padding: 0.5rem;
		background: white;
		color: black;
		width: 2rem;
		height: 2rem;
		font-size: 1rem;
	}

	button:first-child {
		margin-right: 0.5rem;
	}

	button:disabled {
		opacity: 0.5;
	}
</style>
