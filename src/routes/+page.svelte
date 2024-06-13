<script lang="ts">
	import { onMount } from 'svelte';
	let test: HTMLDivElement;
	let text: HTMLTextAreaElement;

	function Save() {}
	onMount(() => {
		text.addEventListener('keydown', (e) => {
			if (e.code === 'Tab') {
				e.preventDefault();
				const startSelection = text.selectionStart;
				const endSelection = text.selectionStart;

				text.value = `${text.value.substring(0, startSelection)}\t${text.value.substring(startSelection, endSelection)}`;
			}
			if (e.code === 'KeyS' && e.ctrlKey) {
				e.preventDefault();
				Save();
			}
		});
	});
</script>

<div bind:this={test} class="bg-blue-800 h-96 w-96">
	<textarea bind:this={text} class="bg-white text-left text-black h-80 w-80 m-auto" />
</div>
