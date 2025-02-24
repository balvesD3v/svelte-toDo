<script lang="ts">
	export let onAdd: (task: string) => void;

	let newTask = '';

	function addTask() {
		if (newTask.trim()) {
			onAdd(newTask);
			newTask = '';
		}
	}
</script>

<div class="flex gap-2">
	<input
		type="text"
		class="w-full rounded-lg border px-4 py-2 focus:ring focus:ring-blue-300"
		bind:value={newTask}
		placeholder="Adicionar nova tarefa..."
	/>
	<button class="rounded-lg bg-blue-500 px-4 py-2 text-white hover:bg-blue-600" on:click={addTask}>
		➕
	</button>
</div>
