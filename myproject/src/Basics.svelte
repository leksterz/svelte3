<script>
	let firstName;
	let lastName;
	$: colour = "red";

	$: fullName = `${firstName} ${lastName}`;
	$: {
		console.log(colour);
		console.log(fullName);
	}
	function changeFunction() {
		colour = "princess";
	}
	function typeFunction(e) {
		colour = e.target.value;
	}
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
	<p>{fullName} - {colour}</p>
	<input type="text" bind:value={firstName} />
	<input type="text" bind:value={lastName} />
	<input on:input={typeFunction} value={colour} type="text" name="" id="" />
</main>
