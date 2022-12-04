<script>
	// GSAP
	import { gsap } from 'gsap';
	import { MotionPathPlugin } from 'gsap/dist/MotionPathPlugin.js';
	import { onMount, onDestroy, beforeUpdate } from 'svelte';

	export let segment;

	const shim = () => {
		let intro = gsap.timeline({
			paused: true,
			repeat: 999,
			repeatDelay: 3,
			yoyo: false
		});

		intro.from('.test', {
			autoAlpha: 0,
			duration: 2,
			x: '0'
		}, '-=1.5');
		intro.to('.test', {
			autoAlpha: 1,
			duration: 3,
			ease: 'expo.inOut',
			x: '100vw'
		});
		intro.to('.test', {
			autoAlpha: 0,
            duration: 1.5
		}, '-=1.5');

		intro.play();
	};

	onMount(() => {
		gsap.registerPlugin(MotionPathPlugin);
		shim();
	});
</script>

<div class="nav-container container-fluid text-light text-center">
	<div class="row h-100 align-items-center">
		<!-- <svg
			x="0px"
			y="0px"
			width="100%"
			height="100%"
			class="shimmer"
			preserveAspectRatio="none"
		>
			<g>
				<path d="M-1.0,0H1325.0" stroke-width="5px" stroke="#111" id="shimmer-path" />
			</g>
		</svg> -->
		<div class="shimmer">
			<div class="test" />
		</div>
		<div class="col-2 h-100 logo-holder">
			<h1>Logo</h1>
		</div>
		<div class="col nav-holder h-100">
			<nav class="nav justify-content-center">
				<a href="/" class="{segment === '/' ? 'active' : ''} nav-link">Home</a>
				<a href="/about" class="{segment === '/about' ? 'active' : ''} nav-link">About</a>
				<a href="/portfolio" class="{segment === '/portfolio' ? 'active' : ''} nav-link"
					>Portfolio</a
				>
			</nav>
		</div>
		<div class="col-2 social-holder h-100">
			<ul>
				<li>E</li>
				<li>F</li>
			</ul>
		</div>
	</div>
</div>

<style>
	.active {
		text-decoration: underline;
	}
	.nav-container {
		height: 90px;
		background-color: #020405;
        border-bottom: 1px solid #333;
	}
	ul {
		list-style: none;
	}
	.logo-holder {
		border-top: 0;
		border-right: 1px solid #333;
	}
	.nav-holder {
		border-top: 0;
		border-right: 1px solid #333;
		position: relative;
	}
	.social-holder {
		z-index: 1;
	}
	.shimmer {
		position: relative;
		top: 89px;
		left: -100px;
		width: calc(100vw + 100px);
		height: 1px;
		padding: 0;
	}
	.test {
		width: 100px;
		height: 2px;
		visibility: hidden;
		z-index: 3;
		position: absolute;
		background: rgb(0, 0, 0);
		background: linear-gradient(90deg, rgba(0, 0, 0, 0) 30%, rgba(255, 255, 255, 1) 100%);
	}
</style>
