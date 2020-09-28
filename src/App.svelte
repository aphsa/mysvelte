<script>
	import Button from "./Button.svelte";
	import { onMount } from "svelte";
	let person = {
		name: "Joe",
		age: 47,
	};
	let string = "<b>Raw html</b>";
	const api_url = "https://api.chucknorris.io/jokes/random";

/*	let users = [];
	onMount(async () => {
		const res = await fetch(`https://jsonplaceholder.typicode.com/users`);
		users = await res.json();
	});
*/
	let message = "";
	onMount(async () => {
		const res = await fetch(api_url);
		message = await res.json();
	});

	let count = 0;
	$: doubleCount = count * 2;
    const handleClick = () => {
    count += 1;
  };
</script>

<main>
	<h1>Hi {person.name}!</h1>
	<p>{@html string}</p>
	{message.value} <br>
	<Button />
	<button on:click={handleClick}>
		Increment
	  </button>
	  <p>{count}  {doubleCount}</p>
	  <form>
		<fieldset>
		   <legend>Selecting elements</legend>
		   <p>
			  <label>Select list</label>
			  <select id = "myList">
				<option value = "1">one</option>
				<option value = "2">two</option>
				<option value = "3">three</option>
				<option value = "4">four</option>
			  </select>
		   </p>
		</fieldset>
	 </form>
</main>
<style>
	main {
		text-align: left;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>