<script>
	import { each } from "svelte/internal";
	import Modal from "./Modal.svelte";
	import AddPersonForm from "./AddPersonForm.svelte";
	let showModal = false;
	let people = [
		{ name: "yoshi", beltColour: "black", age: 25, id: 1 },
		{ name: "mario", beltColour: "orange", age: 45, id: 2 },
		{ name: "luigi", beltColour: "brown", age: 35, id: 3 },
	];
	function handleClick(id) {
		//delete person from people
		people = people.filter((person) => person.id != id);
	}

	function hideModal() {
		showModal = !showModal;
	}

	const addPersonEvent = (e) => {
		const person = e.detail;
		people = [person, ...people];
		showModal = false;
	};
</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
	<Modal {showModal} on:click={() => hideModal()}>
		<AddPersonForm on:addPerson={addPersonEvent} />
	</Modal>
	<button on:click={() => hideModal()}>Add a Person</button>
	{#each people as person (person.id)}
		<div>
			<h2>{person.name}</h2>
			{#if person.beltColour === 'black'}
				<p style={'color: blue'}><strong>true baller</strong></p>
			{/if}
			<p>{person.beltColour} belt, {person.age} years old</p>
			<button
				on:click={() => {
					handleClick(person.id);
				}}>remove</button>
		</div>
	{:else}
		<p>no people bro</p>
	{/each}

	<!-- <div>
		<h4>{people[0].name}</h4>
		<p>{people[0].beltColour}</p>
	</div> -->
</main>
