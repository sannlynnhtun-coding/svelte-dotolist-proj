<script>
	let newItem = '';

	let todoList = [
		{ text: 'Write my first post', status: true },
		{ text: 'Upload the post to the blog', status: false },
		{ text: 'Publish the post at Facebook', status: false }
	];

	function addToList() {
		todoList = [...todoList, { text: newItem, status: false }];
		newItem = '';
	}

	/**
	 * @param {number} index
	 */
	function removeFromList(index) {
		todoList.splice(index, 1);
		todoList = todoList;
	}
</script>

<div style="text-align:center;padding-top:15px;">
	<h1>Welcome to SvelteKit</h1>
	<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
</div>
<br />
<form>
	<input bind:value={newItem} type="text" class="todo-input" />
	<button on:click={addToList} class="todo-button" type="submit">
		<i class="fas fa-plus-square" />
	</button>
</form>
<div class="todo-container">
	<ul class="todo-list">
		{#each todoList as item, index}
			<div class="todo">
				<label for="chk{index}" class={`todo-item ${item.status ? 'completed' : ''}`}>
					<input id="chk{index}" bind:checked={item.status} style="margin-right: 10px;" type="checkbox" />{item.text}
				</label>
				<button on:click={() => removeFromList(index)} class="trash-btn">
					<i class="fas fa-trash" />
				</button>
			</div>
		{/each}
	</ul>
</div>

<style>
</style>
