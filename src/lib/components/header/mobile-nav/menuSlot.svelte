<script lang="ts">
	import Burger from './burger.svelte';
	import SideMenu from './sideMenu.svelte';
	export let open: boolean;
	export let duration = 0.4;
	export let burgerColor = 'rgb(225, 225, 225)';;
	export let menuColor = 'rgb(225, 225, 225)';
	export let width = '80%';
	export let padding = '25px';
	export let paddingTop = '50px';
	export let backgroundColor = 'rgb(198, 16, 16)';
	let burgerProps = {
		duration: duration,
		burgerColor: burgerColor,
		menuColor: menuColor
	};
	let menuProps = {
		duration: duration,
		width: width,
		padding: padding,
		paddingTop: paddingTop,
		backgroundColor: backgroundColor,
		menuColor: menuColor
	};
</script>

<Burger {...burgerProps} bind:open />

<SideMenu {...menuProps} bind:open>
	<slot />
</SideMenu>