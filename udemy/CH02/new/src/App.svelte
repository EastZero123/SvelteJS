<script>
	import ContactCard from "./ContactCard.svelte";

	let name = 'Max';
	let title = ""
	let image = ""
	let description = ""
	let age = 30;

	$: uppercaseName = name.toUpperCase()

	function incrementAge() {
		age += 1;
	}

	function changeName() {
		name = "CHOI"
	}

	function nameInput(event) {
		const enteredValue = event.target.value
		name = enteredValue
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click={incrementAge}>Change Age</button>
<!-- <button on:click="{changeName}">Change Name</button>
<input type="text" value="{name}" on:input="{nameInput}"> -->
<input type="text" bind:value={name}/>
<input type="text" bind:value={title}/>
<input type="text" bind:value={image}/>
<textarea rows="3" bind:value={description}></textarea>

<ContactCard userName={name} jobTitle={title} {description} userImage={image} />