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

<div class="{size} m-auto container relative flex items-center" style="animation-duration: {2 / speed}s;">
	{#each [0, -0.835, -0.668, -0.501, -0.334, -0.167] as item}
		<div
			class="dot absolute left-0 right-0 flex"
			style="animation-duration: {2 / speed}s; animation-delay: calc({2 / speed}s * {item} * 0.5);"
		>
			<div
				class="w-1.5 h-1.5 rounded-full{colorClass()}"
				style="background-color: {customColor[0]}; animation-delay: calc({2 / speed}s * {item} * 0.5);"
			></div>
		</div>
	{/each}
</div>

<style>
	.container {
		/* --uib-speed: 1.5s; */
		animation: smoothRotate linear infinite;
	}

	.dot {
		animation: rotate ease-in-out infinite;
	}

	@keyframes rotate {
		0% {
			transform: rotate(0deg);
		}
		65%,
		100% {
			transform: rotate(360deg);
		}
	}

	@keyframes smoothRotate {
		0% {
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(360deg);
		}
	}
</style>
