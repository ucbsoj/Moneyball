<script>
	const {
		src,
		caption,
		loop = false,
		autoplay = false,
		controls = true,
		customControls = false
	} = $props();

	let videoEl = $state();

	$inspect(videoEl);

	const onClick = () => {
		videoEl.play();
	}

	const restart = () => {
		videoEl.currentTime = 0;
		videoEl.pause();
	}
</script>

<figure>
	<video bind:this={videoEl} {src} {loop} {autoplay} {controls} playsinline></video>

	{#if caption}
		<figcaption>{@html caption}</figcaption>
	{/if}

	<button onclick={onClick}>play</button>
	<button onclick={restart}>restart</button>
</figure>

<style>
	figure {
		width: 100%;
		height: 100%;
	}

	video {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	figcaption {
		text-align: center;
		font-size: 14px;
		margin-top: 8px;
	}
</style>
