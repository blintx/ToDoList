<script lang="ts">
	export let shown = false;
	export let creatingWindowElement: HTMLDivElement;
	function getInfo() {}
</script>

{#if shown}
	<div bind:this={creatingWindowElement} class="flex m-auto w-screen h-screen bg-blue-600"></div>
{/if}
