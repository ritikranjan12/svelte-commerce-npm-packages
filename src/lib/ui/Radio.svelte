<script>
	import { createEventDispatcher } from 'svelte';
	import { nanoid } from 'nanoid';

	const dispatch = createEventDispatcher();

	export let modelValue, 
	export let value;

	let checked = false;

	if (modelValue === value) {
		checked = true;
	}
</script>

<label class="flex items-center gap-2">
	<input
		type="radio"
		id={value + nanoid()}
		name={value}
		{checked}
		{value}
		class="mt-0.5 h-4 w-4 shrink-0 text-primary-500 focus:ring-0 focus:ring-offset-0"
		bind:group={modelValue}
		on:change={() => dispatch('change', modelValue)}
	/>

	<span class="max-w-max text-sm">
		<slot />
	</span>
</label>
