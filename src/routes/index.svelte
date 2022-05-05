<script lang="ts">
	import '../app.scss';
	let counter = 0;
	let counterOperation: 'increment' | 'decrement' = 'increment';

	const changeOperation = () =>
		(counterOperation = counterOperation == 'increment' ? 'decrement' : 'increment');
	const increment = () => counter++;
	const decrement = () => counter--;
	const resetCounter = () => (counter = 0);
</script>

<div class="utils">
	<div class="utils-btn" on:click={changeOperation}>
		{counterOperation == 'increment' ? 'decrement' : counterOperation}
	</div>

	<div class="utils-btn" on:click={resetCounter}>Reset</div>
</div>

<div class="box">
	<div class="counter-display">{counter}</div>
	<div class="counter-controls">
		{#if counterOperation == 'increment'}
			<div class="control-btn" on:click={increment}>+</div>
		{:else}
			<div class="control-btn" on:click={decrement}>-</div>
		{/if}
	</div>
</div>

<style lang="scss">
	.utils {
		position: absolute;
		bottom: 50px;
		left: 0;
		padding: 0px 50px;
		display: flex;
		width: 100%;

		&-btn {
			padding: 15px 20px;
			background: #eee;
			font-size: 21px;
			border-radius: 12px;
			text-transform: capitalize;
			margin-right: 50px;
		}
	}

	.box {
		width: 100%;
		max-width: 500px;
		padding: 20px;
		display: flex;
		flex-direction: column;
		gap: 100px;
	}

	.counter-display {
		width: 50px;
		font-size: 50px;
		margin: auto;
	}

	.counter-controls {
		width: 70%;
		margin: auto;
		background: #f1f1f1;
	}

	.control-btn {
		padding: 70px;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 50px;
		font-weight: bold;
		width: 100%;
		height: 100%;

		&:active {
			background: #eee;
		}
	}
</style>
