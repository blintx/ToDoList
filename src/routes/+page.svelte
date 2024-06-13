<script lang="ts">
	import { onMount } from 'svelte';
	import Textbox from '../textbox.svelte';
	let plusbtn: HTMLDivElement;
	let screen: HTMLDivElement;
	function createNewTextbox() {}
	onMount(() => {
		plusbtn.addEventListener('click', (e) => {
			e.preventDefault();
			createNewTextbox();
		});
	});
</script>

<div bind:this={screen}>
	<div bind:this={plusbtn} class="bg-blue-800 rounded-full w-40 h-40 fixed bottom-2 right-2"></div>
</div>
