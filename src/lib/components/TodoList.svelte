<script lang="ts">
	import { writable } from 'svelte/store';
	import TaskInput from './TaskInput.svelte';
	import TodoItem from './TodoItem.svelte';

	const tasks = writable<string[]>([]);

	function addTask(task: string) {
		tasks.update((t) => [...t, task]);
	}

	function removeTask(index: number) {
		tasks.update((t) => t.filter((_, i) => i !== index));
	}
</script>

<div class="w-full max-w-md rounded-lg bg-white p-6 shadow-lg">
	<h1 class="mb-4 text-center text-2xl font-bold">📋 To-Do List</h1>

	<TaskInput onAdd={addTask} />

	<ul class="mt-4 space-y-2">
		{#each $tasks as task, index}
			<TodoItem {task} {index} onRemove={removeTask} />
		{/each}
	</ul>
</div>
