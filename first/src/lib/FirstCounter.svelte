<script>
	import { counter as myCounter } from './my-first-counter.svelte.js';
</script>

<button onclick={() => (myCounter.count += 1)}>
	clicks: {myCounter.count}
</button>
