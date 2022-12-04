<script>
	// GSAP
	import { gsap } from 'gsap';
	import { ScrollTrigger } from 'gsap/dist/ScrollTrigger.js';
	import { onMount, onDestroy, beforeUpdate } from 'svelte';


	const intro = () => {
		var intro = gsap.timeline({
			paused: true
		});

		intro.from('h1', {
			scale: 0,
			duration: 1,
			autoAlpha: 0,
			ease: 'Power4.inOut'
		});

		intro.play();
	};

	const outro = () => {
		var outro = gsap.timeline({
			paused: true
		});

		outro.to('h1', {
			scale: 0,
			duration: 1,
			autoAlpha: 0,
			ease: 'Power4.inOut'
		});

		outro.play();
	};

	// onMount -----------------------------------------------------
	onMount(() => {
		// gsap.registerPlugin(ScrollTrigger);
	});

	// onDestroy -----------------------------------------------------
	onDestroy(() => {
		// ScrollTrigger.getAll().forEach(trigger => trigger.kill());
	});

	export let refresh = '';

	beforeUpdate(() => {
	});
</script>

{#key refresh}
	<div>
        <slot />
	</div>
{/key}
