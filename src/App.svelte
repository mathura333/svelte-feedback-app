<script lang="ts">
	let firstName="Foo";
	let lastName= "Bar";
	let color = "blue";
	let showText = false;
	let users = [{
		id:1,
		name:'Jhon'
	},{
		id:2,
		name:'Sara'
	},{
		id:3,
		name:'Doo'
	}]
	$: name = firstName + " " + lastName;
	const toggle = () => {
		color = color === 'blue' ? "purple" : "blue"
		showText= !showText
		users = [...users, {id:4,name:"new User"}]
	}
</script>

<main>
	<h1 style="color: {color}">Hello {name}!</h1>
	{#if showText}
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{:else}
	<p>Hello Para</p>
	{/if}
	<button on:click={toggle}>Change color</button>
	{#each users as user (user.id)}
	<h3>{user.name}</h3>
	{/each}
</main>

<style>
	main {
		text-align: center;
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

	button{
		cursor: pointer;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>