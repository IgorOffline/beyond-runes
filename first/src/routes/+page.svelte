<script lang="ts">
	import Nested from '$lib/Nested.svelte';
	import FirstCounter from '$lib/FirstCounter.svelte';
	import SpreadProps from '$lib/SpreadProps.svelte';
	let name = 'Svelte';
	let count = $state(99);
	function increment() {
		count += 1;
	}
	let numbers = $state([1, 2, 3, 4]);
	function addNumber() {
		//numbers[numbers.length] = numbers.length + 1;
		numbers.push(numbers.length + 1);
		//console.log($state.snapshot(numbers));
	}
	let total = $derived(numbers.reduce((t, n) => t + n, 0));
	$inspect(numbers).with((inspected) =>
		console.log(`inspected= ${inspected}, numbers= ${numbers}`)
	);
	const spread = {
		name: 'name1',
		version: 'version1',
		description: 'description1',
		website: 'website1'
	};
	const myEach = [0, 0, 0];
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<button onclick={increment}>
	Clicked {count}
</button>
<button onclick={addNumber}>
	Clicked {numbers}
</button>
<p>{numbers.join(' + ')} = {total}</p>
<Nested answer={2} />
<Nested />
<Nested answer={6} />
<FirstCounter />
<FirstCounter />
<FirstCounter />
<SpreadProps {...spread} />
{#if count < 100}
	<p>(1)</p>
{:else if count > 102}
	<p>(3)</p>
{:else}
	<p>(2)</p>
{/if}
{#each myEach as me, i}
	({i}) {me}<br />
{/each}
