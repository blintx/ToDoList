<script lang="ts">
	import { onMount } from 'svelte';
	let text: HTMLTextAreaElement;
	export let Title = '';

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

<div class="bg-blue-800 h-[34rem] w-[44rem] align-middle content-center">
	<textarea
		bind:this={text}
		class="bg-white text-left text-black h-[90%] w-[90%] m-auto resize-none flex font-semibold"
	/>
</div>
