<script>
	export let total;
	export let totalArr;
	export let buttons;
</script>

<div class="calculator">
	<div id="display">
		{#if total !== 'err'}
			<div>
				<div class="top">{totalArr.join(' ')}</div>
			</div>
			<div>
				<div class="bottom">{total}</div>
			</div>
		{:else}
			<div>{total}</div>
		{/if}
	</div>
	{#each buttons as button}
		<button id={button.id} on:click={button.func}>{button.value}</button>
	{/each}
</div>

<style>
	.calculator {
		display: grid;
		grid-template-columns: 24% 24% 24% 24%;
		grid-gap: 3px;
		background-color: rgb(226, 226, 226);
		box-shadow: 0px 0px 16px 2px #ccc;
		border-radius: 8px;
		margin: 5vh auto;
		width: 70vw;
		max-width: 250px;
		min-width: 200px;
		padding: 5px;
		user-select: none;
		justify-content: space-around;
		align-items: stretch;
		align-content: space-evenly;
        -webkit-tap-highlight-color: transparent;
	}

	#display {
		grid-column: 1 / span 4;
		height: 120px;
		border: solid 2px black;
		border-radius: 2px;
		cursor: initial;
		padding: 0 5px;
		margin-bottom: 1rem;
		font-family: 'VT323';
		background-color: #f4f4f4;
        -webkit-tap-highlight-color: transparent;
	}

	#display > div {
		text-align: right;
		box-sizing: border-box;
		height: 70%;
		width: 100%;
		margin-left: auto;
		margin-right: auto;
		text-align: right;
		overflow: hidden;
		white-space: nowrap;
	}

	#display > div > div {
		float: right;
	}

	.top {
		font-size: 1.3em;
		line-height: 200%;
	}

	.bottom {
		font-size: 2em;
		line-height: 100%;
	}

	button {
		background-color: #f4f4f4;
		color: black;
		border-radius: 5px;
        border: none;
		text-align: center;
		text-decoration: none;
		outline: none !important;
		font-family: 'VT323';
		font-weight: 400;
		font-size: 1.2em;
		transition-duration: 0.4s;
		cursor: pointer;
		box-shadow: 0 4px #999;
		-webkit-tap-highlight-color: transparent;
	}

	button:active {
		background-color: #cecece;
		outline: none !important;
		box-shadow: 0 0.5px #666;
		transform: translateY(4px);
		-webkit-tap-highlight-color: transparent;
	}

	#ac {
		grid-column: 1 / span 2;
	}

	#clear {
		grid-column: 3 / span 2;
	}

	#add {
		height: initial;
		grid-column: 4;
		grid-row: 4 / span 2;
	}
	#equal {
		height: initial;
		grid-column: 4;
		grid-row: 6 / span 2;
	}
	#zero {
		grid-column: 1 / span 2;
	}
</style>
