<script>
	// GSAP
	import { gsap } from 'gsap';
	import { ScrollTrigger } from 'gsap/dist/ScrollTrigger.js';
	import { onMount, onDestroy, beforeUpdate } from 'svelte';

	const scroll = () => {
		var scroll = gsap.timeline({});

		scroll.to('.home', {
				scale: 3,
				transformOrigin: 'center 10%',
				autoAlpha: 0,
				ease: 'ease.inOut',
				scrollTrigger: {
					trigger: '.home',
					pin: false,
					// pinSpacing: 'false',
					// pinSpacer: '.custom-spacer',
					start: 'top top',
					end: '+=900',
					scrub: 1
					// markers: true
				}
			})
			.to('.home', {
				scale: 1,
				duration: 0.1
			})
			.from('.home-s2', {
				scale: 1.5,
				transformOrigin: 'center center',
				autoAlpha: 0,
				ease: 'ease.out',
				scrollTrigger: {
					trigger: '.home-s2',
					pin: false,
					start: '55% bottom',
					end: '+=500',
					scrub: 0.2
					// markers: true
				}
			});
	};

	const textAnim = () => {
		var tl = gsap.timeline({
            paused: true
        });
		tl.to('.text-anim', {
			y: '0',
			duration: 1,
			delay: 1.5,
			ease: 'expo.out(1.5)',
            stagger: 0.1
		});
        tl.play()
	};
	// onMount -----------------------------------------------------
	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);
        textAnim();
		scroll();
	});

	// onDestroy -----------------------------------------------------
	onDestroy(() => {
		// ScrollTrigger.getAll().forEach((trigger) => trigger.kill());
	});

	beforeUpdate(() => {});
</script>

<main>
	<section class="container-fluid text-light home p-0">
		<div class="row">
			<div class="col-12">
				<div class="birds">
					<video autoplay loop width="100%" muted>
						<source src="/images/birds.mp4" type="video/mp4" />
					</video>
				</div>
				<img src="/images/windows-masked.png" alt="" class="img-fluid" />
			</div>
			<div class="textWrapper first">
				<h1 class="text-anim" id="first">Hello</h1>
				<!-- <h1 class="text-anim">World</h1> -->
			</div>
			<div class="textWrapper second">
				<h1 class="text-anim" id="second">World</h1>
			</div>
		</div>
	</section>
	<section class="container-fluid text-light home-s2 p-0">
		<div class="row">
			<div class="col-12 section2-inner">
				<div class="birds2">
					<video autoplay loop width="100%" muted>
						<source src="/images/birds.mp4" type="video/mp4" />
					</video>
				</div>
			</div>
		</div>
	</section>
</main>

<style>
	.home .birds {
		width: 100%;
		height: 100%;
		position: absolute;
		top: 0;
		left: 0;
		z-index: -1;
	}
	.home {
		max-height: 100vh;
		overflow: hidden;
	}
	.home-s2 {
		height: 100%;
	}
	.section2-inner {
		position: relative;
		height: 100vh;
		width: 100vw;
	}
	.birds2 {
		position: absolute;
		top: 90px;
		left: 0;
	}
	main {
		overflow: hidden;
	}
	.textWrapper {
		position: absolute;
		overflow: hidden;
	}
    .textWrapper.first {
        top: 30%;
		left: 5%;
		width: 550px;
		height: 8rem;
    }
    .textWrapper.second {
        top: 50%;
		left: 15%;
		width: 550px;
		height: 8rem;
    }
	.textWrapper > #first {
		position: relative;
	}

    #first,
    #second {
        transform: translate(0, 250px);
    }

	h1 {
		font-family: 'Philosopher', sans-serif;
		font-size: 8rem;
	}
</style>
