<script lang="ts">
	import Nested from '$lib/Nested.svelte';
	let name = 'Svelte';
	let count = $state(99);
	function increment() {
		count += 1;
	}
	let numbers = $state([1, 2, 3, 4]);
	function addNumber() {
		//numbers[numbers.length] = numbers.length + 1;
		numbers.push(numbers.length + 1);
	}
	let total = $derived(numbers.reduce((t, n) => t + n, 0));
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<button onclick={increment}>
	Clicked {count}
</button>
<button onclick={addNumber}>
	Clicked {numbers}
</button>
<p>{numbers.join(' + ')} = {total}</p>
<Nested />
<Nested />
<Nested />
