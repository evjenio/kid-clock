<script>
	import { onMount } from 'svelte';

	let date = new Date();
	const calc = () => {
		return {
			hours: ((date.getHours() + 11) % 12) + 1,
			minutes: date.getMinutes(),
			seconds: date.getSeconds(),
			mills: date.getMilliseconds()
		};
	};
	
	let result = calc()

	$: hour = result.hours * 30;
	$: minute = result.minutes * 6;
	$: second = result.seconds * 6 + (result.mills / 1000) * 6;

	onMount(() => {
		const interval = setInterval(() => {
			date = new Date();
			result = calc();
		}, 50);

		return () => {
			clearInterval(interval);
		};
	});
</script>

<section>
	<div class="clock">
		<div class="wrap">
			<span class="hour" style="transform: rotate({hour}deg);"></span>
			<span class="minute" style="transform: rotate({minute}deg);"></span>
			<span class="second" style="transform: rotate({second}deg);"></span>
			<span class="dot"></span>
		</div>
	</div>
</section>

<style>
	section {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.clock {
		border-radius: 100%;
		background: var(--range-border-color);
		font-family: 'Montserrat';
		border: 5px solid var(--switch-background-color);
		box-shadow: inset 2px 3px 8px 0 rgba(0, 0, 0, 0.1);
	}

	.wrap {
		overflow: hidden;
		position: relative;
		width: 350px;
		height: 350px;
		border-radius: 100%;
	}

	.minute,
	.hour {
		position: absolute;
		height: 100px;
		width: 6px;
		margin: auto;
		top: -28%;
		left: 0;
		bottom: 0;
		right: 0;
		background: var(--contrast);
		transform-origin: bottom center;
		transform: rotate(0deg);
		box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.4);
		z-index: 1;
	}

	.minute {
		position: absolute;
		height: 130px;
		width: 4px;
		top: -38%;
		left: 0;
		box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.4);
		transform: rotate(90deg);
	}

	.second {
		position: absolute;
		height: 100px;
		width: 2px;
		margin: auto;
		top: -28%;
		left: 0;
		bottom: 0;
		right: 0;
		border-radius: 4px;
		background: var(--primary);
		transform-origin: bottom center;
		transform: rotate(180deg);
		z-index: 1;
	}

	.dot {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		width: 12px;
		height: 12px;
		border-radius: 100px;
		background: white;
		border: 2px solid #1b1b1b;
		border-radius: 100px;
		margin: auto;
		z-index: 1;
	}
</style>
