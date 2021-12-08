<script lang="ts">
	async function getRandomName(){
		return await fetch("https://random-data-api.com/api/name/random_name")
			.then(response => response.json())
			.then(data => data.name);
	}

	let promise = getRandomName();
	function newName(){
		promise=getRandomName();
	}
</script>

<button on:click="{newName}">
	get Random Name
</button>

{#await promise}
	<p>.......</p>
{:then nombre} 
	<p>nombre:{nombre}</p>
{/await}