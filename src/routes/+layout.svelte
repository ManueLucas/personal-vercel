<script>
	import Backdrop from "./Backdrop.svelte";
	import "./styles.css";
	import { fly } from "svelte/transition";
	import Page from "./+page.svelte";
	import ProjectSection from "./ProjectSection.svelte";
	import ExperienceSection from "./ExperienceSection.svelte";

	let viewState = "mid";
</script>

<div class="app">
	<main>
		<Backdrop>
			<div class="row movable-element {viewState}">
				<div class="">
					<ProjectSection />
				</div>
				<div class="page">
					<Page bind:leftRightTransitionState={viewState} />
				</div>
				<ExperienceSection />
			</div>
		</Backdrop>
	</main>
</div>

<style>
	    .project-section-wrapper {
        flex: 1;
        overflow-y: auto; /* Allow vertical scrolling */
        height: 100vh; /* Ensure it covers the full viewport height */
        position: relative;
    }
	.page {
		display: flex;
		justify-content: center;
		align-self: center;
		overflow: hidden;
		height: 100vh; /* Ensures the height covers the full viewport */
		width: 100vw; /* Ensures the width covers the full viewport */
		position: relative;
	}
	.movable-element {
		transition: transform 0.5s ease; /* Smooth transition */
	}

	.left {
		transform: translateX(80%); /* Move left */
	}

	.right {
		transform: translateX(-75%); /* Move right */
	}

	.mid {
		transform: translateX(0); /* Center */
	}
	.row {
		display: flex;
		width: 100%;
		position: relative;
	}
	.app {
		display: flex;
		justify-content: center;
		align-self: center;
		overflow: hidden;
		height: 100vh; /* Ensures the height covers the full viewport */
		width: 100vw; /* Ensures the width covers the full viewport */
		position: relative;
	}
	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
