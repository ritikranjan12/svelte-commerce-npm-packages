<script>
	import { createEventDispatcher } from 'svelte';
	import { page } from '$app/stores';
	import { currency } from '@misiki/litekart-utils/dist/utils';

	const dispatch = createEventDispatcher();

	export let disabled = false;
	export let items = [];
	export let name = '';
	export let required = false;
	export let selectedItems = [];
</script>

{#if items?.length}
	<ul class="flex flex-col gap-2">
		{#each items as i}
			{#if i._id}
				<li>
					<label class="inline-flex items-center gap-2">
						<input
							type="checkbox"
							{name}
							id={i._id}
							{disabled}
							{required}
							bind:group={selectedItems}
							value={i._id}
							class="inputcheckbox h-3.5 w-3.5 rounded border border-zinc-200 bg-transparent text-primary-500"
							on:change={() => dispatch('change', selectedItems)}
						/>

						<div class="flex-1 text-sm first-letter:uppercase flex items-center gap-2">
							<img src={i.img} alt={i.name} class="w-8 h-10 object-contain object-center" />

							<p class="flex-1">
								{i.name} at
								{currency(i.price, $page.data?.store?.currencySymbol)}
							</p>
						</div>
					</label>
				</li>
			{/if}
		{/each}
	</ul>
{/if}

<style>
	@media (max-width: 768px) {
		.filter-container {
			max-height: 515px;
			overflow: auto;
		}
	}
	@media (min-width: 768px) {
		.filter-container {
			max-height: 400px;
			overflow: auto;
		}
	}
	input[type='search']::-webkit-search-cancel-button {
		display: none;
	}
</style>
