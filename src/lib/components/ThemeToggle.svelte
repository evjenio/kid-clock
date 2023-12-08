<script>
	function toggle() {
		const theme = window.document.documentElement.dataset.theme;
		window.document.documentElement.dataset.theme = theme == 'dark' ? 'light' : 'dark';
	}
</script>

<label for="theme">
    Dark
	<input type="checkbox" role="switch" id="theme" name="theme" on:click={toggle} />
    Light
</label>

<style>
</style>
