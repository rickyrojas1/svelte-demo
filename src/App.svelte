<script>
	import { fade, fly } from "svelte/transition";
	export let count = 69;
	export let color = "red";
	export let number;
	export let newName = "";
	export let textVal = "Binding is so Easy";
	export let names = ["Ricky", "Jesse", "Matt", "Jonny"];

	let handleDecrement = () => count--;
	let randomNumer = () => (number = Math.random() * 100);
	let addPerson = e => {
	  names = [...names, newName];
	  newName = "";
	};
</script>

<style>
	h1 {
	  color: green;
	  text-align: center;
	  margin-top: 30px;
	}
	p {
	  text-align: center;
	}
	.button-container {
	  margin: auto;
	  display: flex;
	  justify-items: center;
	  width: 40%;
	  margin-top: 30px;
	}
	button {
	  text-align: center;
	  margin: auto;
	  width: 270px;
	  height: 30px;
	}
	input {
	  display: flex;
	  margin: auto;
	  width: 270px;
	  height: 30px;
	}
	ul {
	  display: table;
	  margin: 0 auto;
	}
	.red {
	  color: red;
	}
</style>

<div>
	<h1 transition:fly>Count:  {count}!</h1>
	<div class="button-container">
<button on:click={ () => count ++}  style={count < 69? 'color: green': '' } >
CLICK ME TO ADD ONE
</button>
<button on:click={ handleDecrement}  class={count > 69? 'red': '' }>
CLICK ME TO MINUS ONE
</button>
	</div>
<hr>
</div>


<div>
<h1>Random Number Generator: </h1>
<p>{number ? number : ''}</p>
{#if number >= 69}
	<p in:fly={{ x: 1000, duration: 500}} out:fly={{ x: 500, duration: 500}}>We got a winner 🤑🤑🤑</p>
{:else if number < 69}
	<p in:fly={{ y: 1000, duration: 500}} out:fly={{ y: 500, duration: 500}}>Loser 💩💩💩</p>
{/if}
	
	<div class="button-container">
<button on:click={ randomNumer}  >
CLICK ME FOR RANDOM NUMBER
</button>
	</div>
<hr>
</div>

<div>
<h1>{textVal}</h1>
<input bind:value={textVal} type="text">
<hr>
</div>



<div>
<h1>List of Names</h1>
<ul>
{#each names as name}
	<li>{name}</li>
	{:else}
		<p>We aint got nobody</p>
{/each}
</ul>
<div class="button-container">
<input  bind:value={newName}  type="text">
<button on:click={addPerson} disabled={newName === ''}>Add Person</button>
</div>
<hr>
</div>


