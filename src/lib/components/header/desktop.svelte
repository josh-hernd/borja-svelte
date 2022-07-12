<script lang="ts">
import { page } from "$app/stores";
</script>

<nav>
	{#if $$props.NavData.length > 3}
		<!-- if nav items is more than 3 split in half and align evenly -->
		<ul>
			{#each $$props.NavData.slice(0, $$props.NavData.length / 1.6) as liItem}
				<li class:active={$page.url.pathname === liItem.url}><a href={liItem.url}>{liItem.label}</a></li>
			{/each}
		</ul>

		<ul>
			{#each $$props.NavData.slice($$props.NavData.length / 1.6) as liItem}
				{#if liItem.type === 'call-button'}
					<li><a class={liItem.type} href="tel:+{liItem.url}">{liItem.label}</a></li>
				{:else}
					<li class:active={$page.url.pathname === liItem.url}><a href={liItem.url}>{liItem.label}</a></li>
				{/if}
			{/each}
		</ul>
	{:else}
		<!-- if nav items is less than 3  -->
		<ul>
			{#each $$props.NavData as liItem}
				{#if liItem.type === 'call-button'}
					<li><a class={liItem.type} href="tel:+{liItem.url}">{liItem.label}</a></li>
				{:else}
					<li class:active={$page.url.pathname === liItem.url}><a href={liItem.url}>{liItem.label}</a></li>
				{/if}
			{/each}
		</ul>
	{/if}
</nav>

<style lang="sass">

nav
	--svgFill: rgb(198, 16, 16)
	width: 100%
	position: relative
	padding: 35px 0
	position: relative
	background: linear-gradient(180deg, var(--svgFill) 50%, rgba(255,255,255,0) 50%)
	display: flex
	justify-content: space-around
	z-index: 1
	ul
		display: flex
		align-items: center
		margin: 0
		padding: 0
		li
			margin: 0 12px
			padding-bottom: 5px
.active
	border-bottom: 1px solid #fff
.call-button
	padding: 8px 32px
	background: #C61010
	border: 3px solid #FFFFFF
	border-radius: 3px
	box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.2)
</style>
