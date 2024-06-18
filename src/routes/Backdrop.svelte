<script lang='ts'>
    import {spring} from 'svelte/motion'
	import {get} from 'svelte/store'
	import {onMount} from 'svelte'
    import {paint} from './gradient.js'
	
	var w = 0
	var h = 0
	let pointerL1 = spring(0, {
		stiffness: 0.1,
		damping: 1
	})

	onMount(() => {
		w = window.innerWidth;
		h = window.innerHeight;
		const canvas= document.getElementById('backdrop');
		const context = (canvas).getContext('2d');

		let frame = requestAnimationFrame(function loop(t) {
			frame = requestAnimationFrame(loop);
			paint(context, t);
		});

		return () => {
			cancelAnimationFrame(frame);
		};
	});
</script>


<canvas
	on:mousemove={(e) => {
		pointerL1.set((e.clientX + e.clientY) / (h + w))
	}}
    id={'backdrop'}
	width={32}
	height={32}

/>
<slot/>

<style>
	canvas {
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		background-color: #666;
		z-index: -1;
	}
</style>