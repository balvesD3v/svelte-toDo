<script context="module" lang="ts">
	import { writable } from 'svelte/store';
	import TaskInput from './TaskInput.svelte';
	import TodoItem from './TodoItem.svelte';

	export type Task = {
		text: string;
		done: boolean;
	};

	const tasks = writable<Task[]>([]);

	function addTask(taskText: string) {
		tasks.update((t) => [...t, { text: taskText, done: false }]);
	}

	function removeTask(index: number) {
		tasks.update((t) => t.filter((_, i) => i !== index));
	}

	function toggleTask(index: number) {
		tasks.update((t) => t.map((task, i) => (i === index ? { ...task, done: !task.done } : task)));
	}
</script>

<div class="w-full max-w-md rounded-lg bg-white p-6 shadow-lg">
	<h1 class="mb-4 text-center text-2xl font-bold">📋 To-Do List</h1>

	<TaskInput onAdd={addTask} />

	<ul class="mt-4 space-y-2">
		{#each $tasks as task: Task, index}
			<TodoItem {task} {index} onRemove={removeTask} onToggle={toggleTask} />
		{/each}
	</ul>
</div>
