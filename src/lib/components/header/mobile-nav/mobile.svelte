<script lang="ts">
    import { page } from '$app/stores';
	import MenuSlot from './menuSlot.svelte';
	let open: boolean;
	let position = 'fixed';

</script>

<nav style="--is-fixed: {position};">
	<MenuSlot bind:open>

		<ul>
			{#each $$props.NavData as liItem}
				{#if liItem.type === 'call-button'}
					<li><a class={liItem.type} href="tel:+{liItem.url}" sveltekit:prefetch on:click={()=> (open = !open)}>{liItem.label}</a></li>
				{:else}
					<li class:active={$page.url.pathname === liItem.url}><a href={liItem.url} sveltekit:prefetch on:click={()=> (open = !open)}>{liItem.label}</a></li>
				{/if}
			{/each}
		</ul>

	</MenuSlot>
</nav>

<style lang="sass">
nav
    width: auto
    padding: 14px
    position: var(--is-fixed)
    bottom: 12px
    right: 12px
    background: rgb(198, 16, 16)
    border-radius: 100%
    box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.2)
    z-index: 10

ul
    display: flex
    flex-direction: column
    margin: 0
    padding: 0
    li
        list-style-type: none
        margin: 5px 0
        padding-bottom: 5px
        a
            text-decoration: none

.active
    border-bottom: 1px solid #fff

.call-button	
    padding: 8px 32px
    background: #C61010
    border: 3px solid #FFFFFF
    border-radius: 3px
    box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.2)
    display: block
</style>