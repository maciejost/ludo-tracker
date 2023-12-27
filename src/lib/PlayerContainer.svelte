<script lang="ts">
	export let playerColor: Player
	export let game: Game
	export let updateGame: (player: Player, powerUp: keyof PowerUps, value: number) => void
</script>
<div>
	<h2>
		{playerColor}
	</h2>
	<div>
		<p>Double throw</p>
		<p>{game[playerColor].double}</p>
		<button
			on:click={() => updateGame(playerColor, 'double', game[playerColor].double + 1)}
		>
			+1
		</button>
		<button
			disabled={game[playerColor].double === 0}
			on:click={() => updateGame(playerColor, 'double', game[playerColor].double - 1)}
		>
			-1
		</button>
	</div>
	<div>
		<p>Choose throw</p>
		<p>{game[playerColor].choose}</p>
		<button

			on:click={() => updateGame(playerColor, 'choose', game[playerColor].choose + 1)}
		>
			+1
		</button>
		<button
			disabled={game[playerColor].choose === 0}
			on:click={() => updateGame(playerColor, 'choose', game[playerColor].choose - 1)}
		>
			-1
		</button>
	</div>
	<div>
		<p>Shield</p>
		<p>{game[playerColor].shield}</p>
		<button
			on:click={() => updateGame(playerColor, 'shield', game[playerColor].shield + 1)}
		>
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