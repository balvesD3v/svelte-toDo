<script context="module" lang="ts">
	import type { Task } from './TodoList.svelte';

	export let task: Task;
	export let index: number;
	export let onRemove: (index: number) => void;
	export let onToggle: (index: number) => void;
</script>

<li class="flex items-center justify-between rounded-lg bg-gray-200 p-2">
	<div class="flex items-center gap-2">
		<button class="text-green-500 hover:text-green-700" onclick={() => onToggle(index)}>
			{task.done ? '✅' : '⏳'}
		</button>
	</div>
	<span class={task.done ? 'text-gray-500 line-through' : ''}>{task.text}</span>
	<button class="text-red-500 hover:text-red-700" onclick={() => onRemove(index)}> ❌ </button>
</li>
