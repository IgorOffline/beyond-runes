<script lang="ts">
	import Nested from '$lib/Nested.svelte';
  let name = 'Svelte';
</script>

<h1>Hello {name.toUpperCase()}!</h1>
<Nested />
<Nested />
<Nested />