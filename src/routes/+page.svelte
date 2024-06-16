<script lang="ts">
	import { onMount } from 'svelte';
	import Textbox from '../textbox.svelte';
	import CreatingWindow from '../creatingWindow.svelte';
	import getInfo from '../creatingWindow.svelte';
	let plusbtn: HTMLDivElement;
	let screen: HTMLDivElement;
	let creatingWindowElement: HTMLDivElement;
	let shown = false;
	const outputTitle: string[] = [];

	function createNewTextbox() {
		shown = true;
		const title = outputTitle[0];
		const subTitle = outputTitle[0];

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
	<CreatingWindow {shown} {creatingWindowElement} output={outputTitle}></CreatingWindow>
</div>
