<script>
	import WeatherNight from 'virtual:icons/mdi/weather-night';
	import WhiteBalanceSunny from 'virtual:icons/mdi/white-balance-sunny';

	function toggle() {
		const theme = window.document.documentElement.dataset.theme;
		window.document.documentElement.dataset.theme = theme == 'dark' ? 'light' : 'dark';
	}
</script>

<form>
	<WhiteBalanceSunny />
	<input type="checkbox" role="switch" id="theme" name="theme" on:click={toggle} />
	<WeatherNight />
</form>

<style>
	input {
		margin: 0;
		padding: 0;
	}
</style>
