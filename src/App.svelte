<script>
	import { fade, fly } from "svelte/transition";
	export let count = 69;
	export let color = "red";
	export let number;
	export let textVal = "Binding is so Easy";

	let handleDecrement = () => count--;
	let randomNumer = () => (number = Math.random() * 100);
</script>

<style>
	h1 {
	  color: green;
	}
	button {
	  width: 300px;
	  height: 40px;
	}
	.red {
	  color: red;
	}
</style>

<div>
	<h1 transition:fly>Count:  {count}!</h1>
<button on:click={ () => count ++}  style={count < 69? 'color: green': '' } >
CLICK ME TO ADD ONE
</button>
<button on:click={ handleDecrement}  class={count > 69? 'red': '' }>
CLICK ME TO MINUS ONE
</button>
<hr>
</div>


<div>
<h1>Random Number Generator: </h1>
<p>{number ? number : 'number undefined'}</p>
{#if number >= 69}
	<p in:fly={{ x: 1000, duration: 500}} out:fly={{ x: 500, duration: 500}}>We got a winner 🤑🤑🤑</p>
{:else if number < 69}
	<p in:fly={{ y: 1000, duration: 500}} out:fly={{ y: 500, duration: 500}}>Loser 💩💩💩</p>
{/if}
<button on:click={ randomNumer}  >
CLICK ME FOR RANDOM NUMBER
</button>
<hr>
</div>

<div>
<input bind:value={textVal} type="text">
<h1>{textVal}</h1>
</div>


