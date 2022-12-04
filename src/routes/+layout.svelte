<script>
	import Nav from '../components/Nav.svelte';
	import PageTransitions from '../components/PageTransitions.svelte';
	import { page } from '$app/stores';

</script>

<Nav segment={$page.url.pathname} />

<PageTransitions refresh="{$page.url.pathname}">
	<slot />
</PageTransitions>
