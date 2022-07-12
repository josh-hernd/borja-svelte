<script lang="ts">
	import { fixedNav } from '$lib/stores/store';
	import MediaQuery from '$lib/components/media/media-query.svelte';
	import DesktopNav from '$lib/components/header/desktop.svelte';
	import MobileNav from '$lib/components/header/mobile-nav/mobile.svelte';

	export let NavData: { id: number; label: string; url: string; type: string }[];

	let NavProps = {
		NavData
	};
</script>

	<MediaQuery query="(min-width: 960px)" let:matches>
		{#if matches}
		<header bind:clientHeight={$fixedNav}>
			<DesktopNav {...NavProps} />
			<img class="arch" src="/svg/arch.svg" alt="" />
		</header>
		{:else}
		<header bind:clientHeight={$fixedNav}>
			<MobileNav {...NavProps} />
			<img class="arch" src="/svg/arch.svg" alt="" />
		</header>
		{/if}
	</MediaQuery>

<style lang="sass">
header
	width: 100%
	position: fixed
	top: 0
	left: 0
	z-index: 10
.arch 
	position: absolute
	bottom: 0
	width: 100%
	height: 100%
	object-fit: cover
	-webkit-filter: drop-shadow( 0px 10px 5px rgba(0, 0, 0, 0.2))
	filter: drop-shadow( 0px 10px 5px rgba(0, 0, 0, 0.2))

</style>
