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

<div class="{size} m-auto flex items-center justify-center">
	{#each [0, 1, 2, 3] as item}
		<div
			class="dot relative flex items-center h-full w-1/4"
			class:dot1={item === 0}
			class:dot2={item === 3}
			style="transform-origin: center top;animation-duration: {1.5 / speed}s;"
		>
			<div class="w-full h-1/4 rounded-full{colorClass()}" style="background-color: {customColor[0]};"></div>
		</div>
	{/each}
</div>

<style>
	.dot1 {
		animation: swing linear infinite;
	}

	.dot2 {
		animation: swing2 linear infinite;
	}

	@keyframes swing {
		0% {
			transform: rotate(0deg);
			animation-timing-function: ease-out;
		}

		25% {
			transform: rotate(70deg);
			animation-timing-function: ease-in;
		}

		50% {
			transform: rotate(0deg);
			animation-timing-function: linear;
		}
	}

	@keyframes swing2 {
		0% {
			transform: rotate(0deg);
			animation-timing-function: linear;
		}

		50% {
			transform: rotate(0deg);
			animation-timing-function: ease-out;
		}

		75% {
			transform: rotate(-70deg);
			animation-timing-function: ease-in;
		}
	}
</style>
