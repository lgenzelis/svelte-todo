<script lang="ts">
	import Item from './Item.svelte'
	export let initialTodo: string;
	let todos = [];
	let newTodo = initialTodo;

	function addTodo() {
		todos = [...todos, { text: newTodo, done: false }]
		newTodo = '';
	}

	function toggleTodo(index) {
		const { text, done } = todos[index];
		const newTodos = todos.slice();
		newTodos[index] = { text, done: !done };
		todos = newTodos;
	}

	function clearDoneTodos() {
		todos = todos.filter(({ done }) => !done)
	}

	$: isAnyTodoDone = todos.some(({done}) => done)

</script>

<main>
	<form on:submit|preventDefault={addTodo}>
		<input bind:value={newTodo} />
		<button disabled={!newTodo.trim().length}>Add ToDo</button>
	</form>
	<ul>
		{#each todos as todo, idx}
			<Item todo={todo} on:click={() => toggleTodo(idx)} />
		{/each}
	</ul>
	<button on:click={clearDoneTodos} disabled={!isAnyTodoDone}>Clear completed tasks</button>
</main>


