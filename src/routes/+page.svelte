<script lang="ts">
	type PowerUps = {
	[key: 'shield' | 'choose' | 'double'] : number
	}

	type Player = 'green' | 'red' | 'blue' | 'yellow'

	type Game = {
		[key in Player]: PowerUps
	}

	let game = {
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

</script>
<main>
	<h1>Ludo World Tracker</h1>
	<p>A companion app for <a href="https://www.facebook.com/RealLudoSuperstar/" target="_blank">Ludo World</a> to help you keep track of your opponents powerups.</p>
</main>