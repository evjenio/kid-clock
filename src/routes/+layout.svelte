<script>
	import ThemeToggle from '$lib/components/ThemeToggle.svelte';
</script>

<header class="container">
	<hgroup>
		<h1>Kid Clock</h1>
		<ThemeToggle />
	</hgroup>
</header>
<main>
	<slot />
</main>

<style>
	hgroup {
		display: flex;
        justify-content: space-between;
        align-items: center;    
	}
</style>
