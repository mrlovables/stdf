<script>
	export let theme = false;
	export let inverse = false;
	export let size = 'w-8 h-8';
	export let customColor = [];
	export let speed = 1;

	const colorClass = () => {
		if (inverse) {
			return theme ? ' bg-dark dark:bg-primary' : ' bg-white dark:bg-black';
		} else {
			return theme ? ' bg-primary dark:bg-dark' : ' bg-black dark:bg-white';
		}
	};
</script>

<div class={`${size} m-auto flex justify-between items-center`}>
	{#each [0, 1, 2] as i}
		<div
			class={`${colorClass()} rounded-full w-2 h-2 loading`}
			style="animation-delay: {i * 100 - 300}ms;background: {customColor[0]};animation-duration: {1 /
				speed}s;-webkit-animation-duration: {1 / speed}s;"
		/>
	{/each}
</div>

<style>
	.loading {
		animation: ball-pulse 1s ease infinite;
	}

	@keyframes ball-pulse {
		0%,
		60%,
		100% {
			opacity: 1;
			transform: scale(1);
		}

		30% {
			opacity: 0.1;
			transform: scale(0.1);
		}
	}
</style>
