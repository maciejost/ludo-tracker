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
			<p>Double throw</p>
			<p>{game[playerColor].double}</p>
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
			<p>Choose throw</p>
			<p>{game[playerColor].choose}</p>
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
			<p>Shield</p>
			<p>{game[playerColor].shield}</p>
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
	}

	.powerups {
		text-align: center;
		display: flex;
		width: 100%;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
	}
</style>
