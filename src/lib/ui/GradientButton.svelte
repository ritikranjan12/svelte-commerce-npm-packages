<script>
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	export let className;
	export let disabled = false;
	export let loading = false;
	export let loadingringsize = 'base';
	export let roundedFull = false;
	export let title = '';
	export let type = 'button';

	// creates a `class` property, even
	// though it is a reserved word

	export { className as class };

	let localLoadingPeriod = false;

	function handleClick() {
		dispatch('click');
		handleLoading();
	}

	function handleLoading() {
		if (loading === false) {
			localLoadingPeriod = true;

			setTimeout(() => {
				localLoadingPeriod = false;
			}, 2000);
		}
	}
</script>

<button
	{type}
	{title}
	{disabled}
	class="relative transform items-center justify-center overflow-hidden bg-white px-4 py-2 text-center font-semibold tracking-wider text-white shadow-md transition duration-700 focus:outline-none focus:ring-0 focus:ring-offset-0 hover:shadow
	{disabled ? 'bg-zinc-400 cursor-not-allowed' : 'gradient active:scale-95'}
    {roundedFull ? 'rounded-full' : 'rounded'}
	{className}"
	on:click={handleClick}
>
	<div class="flex items-center justify-center gap-1">
		<slot />
	</div>

	{#if loading || localLoadingPeriod}
		<div
			class="absolute inset-0 flex cursor-not-allowed items-center justify-center bg-black bg-opacity-70"
		>
			<svg
				class="mx-auto animate-spin text-white
				{loadingringsize == 'xs' ? 'w-4 h-4' : ''}
				{loadingringsize == 'sm' ? 'h-5 w-5' : ''}
				{loadingringsize == 'base' ? 'h-6 w-6' : ''}
				{loadingringsize == 'lg' ? 'h-7 w-7' : ''}"
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
			>
				<circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"
				></circle>
				<path
					class="opacity-75"
					fill="currentColor"
					d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
				></path>
			</svg>
		</div>
	{/if}
</button>

<style>
	.gradient {
		display: flex;
		background: linear-gradient(120deg, #112d4e, #1a6b1a, #112d4e, #1a6b1a, #112d4e);
		background-size: 300%;
		transition: 0.8s;
	}

	.gradient:hover {
		background-position: right;
	}
</style>
