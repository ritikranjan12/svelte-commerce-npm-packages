<script>
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	export let alphaNumeric = false;
	export let autoFocus = false;
	export let disabled = false;
	export let error = false;
	export let id = '';
	export let isAlphaNumeric = null;
	export let name = '';
	export let placeholder = '';
	export let required = false;
	export let success = false;
	export let value = '';
	export let type = 'text';
	export let maxlength;

	let clazz = '';
	export { clazz as class };

	function handleInput() {
		if (alphaNumeric === true) {
			isAlphaNumeric = value.match('^[A-Za-z0-9]+$');

			if (isAlphaNumeric === null) {
				error = true;
			} else {
				error = false;
				dispatch('input');
			}
		} else {
			dispatch('input');
		}
	}
</script>

<div>
	{#if type === 'text'}
		<input
			type="text"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{:else if type === 'email'}
		<input
			type="email"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{:else if type === 'password'}
		<input
			type="password"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{:else if type === 'date'}
		<input
			type="date"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{:else if type === 'time'}
		<input
			type="time"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{:else if type === 'number'}
		<input
			type="number"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{:else if type === 'tel'}
		<input
			type="tel"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{:else if type === 'datetime-local'}
		<input
			type="datetime-local"
			bind:value
			{id}
			{name}
			{autoFocus}
			{maxlength}
			class="w-full rounded border border-zinc-200 p-2 text-sm placeholder-zinc-400 transition duration-300 focus:outline-none focus:ring-1 focus:ring-primary-500 {clazz} 
			{disabled ? 'cursor-not-allowed bg-zinc-100' : 'bg-transparent hover:bg-zinc-50'}
			{success ? 'border-green-500 focus:border-green-500 bg-green-100 focus:ring-green-500' : ''}
			{error ? 'border-red-500 focus:border-red-500 bg-red-100 focus:ring-red-500' : ''}"
			{placeholder}
			{required}
			{disabled}
			aria-label={placeholder}
			on:input={handleInput}
			on:blur={() => dispatch('blur')}
		/>
	{/if}

	{#if alphaNumeric && error}
		<p class="mt-2 text-xs text-red-600">Must contain only letters and numbers with no spaces</p>
	{/if}
</div>
