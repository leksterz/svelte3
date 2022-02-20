<script>
    import { bind } from "svelte/internal";
    import { createEventDispatcher } from "svelte";

    let dispatch = createEventDispatcher();

    let age;
    let name;
    let beltColour;
    let skills = [];
    // let fighting = false;
    // let sliding = true;
    // let trapping = false;
    const handleSubmit = () => {
        const person = {
            name,
            beltColour,
            age,
            skills,
            id: Math.random(),
        };
        dispatch("addPerson", person);
    };
</script>

<style>
</style>

<h3>Add a new person</h3>
<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="first name" bind:value={name} />

    <input type="number" placeholder="age" bind:value={age} />
    <label>Skills:</label>
    <br />
    <input type="checkbox" bind:group={skills} value="fighting" />fighting<br />
    <input type="checkbox" bind:group={skills} value="trapping" />trapping<br />
    <input type="checkbox" bind:group={skills} value="sliding" />sliding<br />
    <br />
    <label>Belt Colour:</label>
    <select bind:value={beltColour}>
        <option value="black">black</option>
        <option value="blue">blue</option>
        <option value="orange">orange</option>
        <option value="red">red</option>
    </select>
    <br />
    <br />
    <button>add person</button>
</form>
