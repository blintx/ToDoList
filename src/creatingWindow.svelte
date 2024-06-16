<script lang="ts">
	import { onMount } from 'svelte';

	export let shown = false;
	export let creatingWindowElement: HTMLDivElement;
	export let output: string[] = [];

	let form: HTMLFormElement;
	onMount(() => {
		form?.addEventListener('submit', (e) => {
			e.preventDefault();
			const data = new FormData(e.target as HTMLFormElement);

			const Title = String(data.get('title'));
			const subTitle = String(data.get('subtitle'));
			output = [Title, subTitle];
			shown = false;
		});
	});
</script>

{#if shown}
	<div bind:this={creatingWindowElement} class="flex w-screen h-screen fixed z-0">
		<div class="bg-blue-600 w-[40rem] h-96 rounded-2xl m-auto content-center">
			<form
				class="grid grid-rows-3 bg-blue-800 w-[36rem] h-80 m-auto content-stretch rounded-2xl"
				bind:this={form}
			>
				<input
					placeholder="Cím"
					type="text"
					name="title"
					class="my-6 mx-2 rounded-2xl placeholder:text-black text-center text-2xl font-bold"
				/>

				<input
					placeholder="Alcím (Nem kötelező)"
					type="text"
					name="subtitle"
					class="my-6 mx-2 rounded-2xl placeholder:text-gray-600 text-center text-2xl font-semibold"
				/>
				<button
					type="submit"
					class="bg-blue-400 text-center text-white font-bold text-2xl my-6 mx-3 rounded-2xl flex items-center justify-center"
				>
					Kész
				</button>
			</form>
		</div>
	</div>
{/if}
