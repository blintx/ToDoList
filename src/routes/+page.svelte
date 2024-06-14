<script lang="ts">
	import { onMount } from 'svelte';
	import Textbox from '../textbox.svelte';
	import CreatingWindow from '../creatingWindow.svelte';
	let plusbtn: HTMLDivElement;
	let screen: HTMLDivElement;
	let creatingWindowElement: HTMLDivElement;
	function GetTitle() {
		let title = 'creatingWindowElement';

		return title;
	}
	function createNewTextbox() {
		let title: string = GetTitle();
		const newTExt = new Textbox({ target: screen, props: { Title: title } });
	}
	onMount(() => {
		plusbtn.addEventListener('click', (e) => {
			e.preventDefault();
			createNewTextbox();
		});
	});
</script>

<div bind:this={screen}>
	<div bind:this={plusbtn} class="bg-blue-800 rounded-full w-40 h-40 fixed bottom-2 right-2"></div>
	<CreatingWindow shown={false} {creatingWindowElement}></CreatingWindow>
</div>
