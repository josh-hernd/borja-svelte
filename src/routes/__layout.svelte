<script type="ts">
	import '../app.sass';
	import { fixedNav } from '$lib/stores/store';

	import Content from '$lib/the-content/content';
	import Nav from '$lib/components/header/nav.svelte';
	import Footer from '$lib/components/footer/footer.svelte';
</script>

<div style="padding-top: {$fixedNav / 2}px;">
	<Nav NavData={Content.NavigationData.header} />
	<slot />
	<Footer preFooter={Content.NavigationData.postEnd} footerData={Content.NavigationData.footer} />
</div>
