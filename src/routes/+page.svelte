<script>
	import { fly, fade } from "svelte/transition";
	import { quintOut } from "svelte/easing";
	import Arrow from "../lib/images//arrow-thick-thin-up-svgrepo-com.svg";
	export let leftRightTransitionState = "mid";

	let m = { x: 0, y: 0 };
	let names = ["Manuel", "Owen", "Lucas"];
	const fullname = names.join(" ");
	let currentNameIndex = 0;
	const cycleNameIndex = () =>
		(currentNameIndex = (currentNameIndex + 1) % 3);
	let clear = 0;

	$: console.log(m.x);
	let hoveringOnName = false;
</script>

<section
	role="article"
	on:mousemove={(event) => {
		m.x = event.clientX;
		m.y = event.clientY;
	}}
	class="col"
>
	<div
		role="article"
		on:mouseleave={() => {
			hoveringOnName = false;
		}}
		on:mouseenter={() => {
			hoveringOnName = true;
		}}
		class="card bg-dark"
	>
		<button
		class="left-arrow-button"
			on:click={() =>
				(leftRightTransitionState =
					leftRightTransitionState == "mid" ? "left" : "mid")}
			role={"switch"}
			class:left-arrow-button-on={leftRightTransitionState=='left'}
		>
			<img
				class="w-25 left-arrow"
				src={Arrow}
				alt="left arrow"
				class:left-arrow-rotated={leftRightTransitionState == "left"}
			/>
			{#if leftRightTransitionState=="mid"}
			<h1>Projects</h1>				
			{:else if leftRightTransitionState=="left"}
			<h1>Back</h1>
			{/if}
		</button>
		<button
			on:click={() =>
				(leftRightTransitionState =
					leftRightTransitionState == "mid" ? "right" : "mid")}
			role={"switch"}
			class="right-arrow-button"
		>
			<img class="w-25 right-arrow" 
			src={Arrow} 
			alt="right arrow" 
			class:right-arrow-rotated={leftRightTransitionState == "right"}
			/>
			{#if leftRightTransitionState=="mid"}
			<h1>Work (WIP)</h1>				
			{:else if leftRightTransitionState=="right"}
			<h1>Back</h1>
			{/if}
		</button>

		<div class=" mt-2 mb-5">
			<div class="px-5 mt-4">
				<h1 class="mx-2 mt-1 name-title">
					<strong>✨Hi, I'm {fullname}✨</strong>
				</h1>
				<br />
				<h1 class="about-paragraph">
					A 4th year Computer Science student at Carleton University
					specializing in machine learning and artificial
					intelligence.
				</h1>
			</div>
		</div>
	</div>
</section>

<style>
	section {
		justify-content: center;
		position: relative;
		width: 50%;
		margin: auto; /* Center the Page section */
	}

	.card {
		transition: width 2s;
		transition-timing-function: ease-in;
		width: 50%;
		background-blend-mode: color-dodge;
		opacity: 90%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin: auto;
	}

	.name-title {
		font-size: 325%;
	}

	.about-paragraph {
		font-family:
			Fira Code,
			monospace;
		font-weight: 500;
		line-height: 150%;
	}

	h1,
	h3,
	h6,
	p {
		position: inherit;
		text-align: center;
		width: 100%;
		color: white;
		font-family: Arial, Helvetica, sans-serif;
	}
	button.left-arrow-button-on{
		left: -40rem
	}

	img + h1{
		font-family:
			Fira Code,
			monospace;
	}
	.left-arrow-button,
	.right-arrow-button {
		transition-duration: 200ms;
		position: absolute;
		font-size: 2rem;
		cursor: pointer;
		background-color: transparent;
		border: none;
		max-width: 90%;
		transition: filter 0.3s;
	}
	.left-arrow {
		rotate: -90deg;
	}
	.left-arrow-button{
		position: absolute;
		left: -35rem;
	}
	.right-arrow-button{
		position: absolute;
		right:-35rem;
	}
	img.left-arrow-rotated {
		rotate: 90deg;
		left: -37rem;
	}
	img.right-arrow-rotated {
		rotate: -90deg;
		right: -37rem;
	}
	.left-arrow + h1{
		position: absolute;
	}
	.right-arrow {
		right: -26rem;
		rotate: 90deg;
	}
	.left-arrow,
	.right-arrow {
		transition: filter 0.3s;
	}
	.left-arrow:hover,
	.right-arrow:hover {
		filter: brightness(3); /* Lighten the image */
		transition-duration: 100ms;
	}
</style>
