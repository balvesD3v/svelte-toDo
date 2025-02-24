<script lang="ts">
	export let task: string;
	export let index: number;
	export let onRemove: (index: number) => void;
</script>

<li class="flex items-center justify-between rounded-lg bg-gray-200 p-2">
	<span>{task}</span>
	<button class="text-red-500 hover:text-red-700" on:click={() => onRemove(index)}> ❌ </button>
</li>
