<!-- 
###############################
This SECTION accepts
    Headline
    Labels with title and icons
    Buttons 
###############################
-->
<script lang="ts">
	import SimpleButton from '../buttons/simpleButton.svelte';
	import IconLabel from '../labels/iconLabel.svelte';

	export let headline: string | undefined;
	export let parag: string | undefined;

	interface badges {
		label?: string | undefined;
		icon?: string | undefined;
	}
	export let reasonBadge: badges[] | undefined;

	interface btnElem {
		title?: string | undefined;
		url?: string | undefined;
	}
	export let button: btnElem;
</script>

<div class="simpleSec">
	<div class="contain">
		<h3>{headline}</h3>

		{#if reasonBadge !== undefined}
			<div class="badges">
				{#each reasonBadge as badge}
					<IconLabel label={badge.label} icon={badge.icon} fontColor="#fff" labelColor="#C61010" />
				{/each}
			</div>
		{/if}
		{#if parag !== undefined}
			<p>{parag}</p>
		{/if}

		{#if button.title !== undefined}
			<SimpleButton
				title={button.title}
				url={button.url}
				fontColor="#fff"
				backgroundColor="#C61010"
				positon="center"
			/>
		{/if}
	</div>
</div>

<style lang="sass">
@use '../../abstract/breakPoints' as *

.simpleSec
    width: calc( 100% - 40px )
    padding: 60px 20px
    display: flex
    justify-content: center
    align-items: center

.contain
    width: 50%
    text-align: center
    h3
        font-size: 30px
        line-height: 36px
        color: #C61010   
    p
        font-size: 17px
        margin: 19px 0
    @include dynamicPoints($min: 200px, $max: 1025px)
        width: 100%
        h3
            font-size: 22px

.badges
    margin: 5px auto
    display: flex
    justify-content: center
    @include dynamicPoints($min: 200px, $max: 1025px)
        width: 60%
        flex-direction: column
</style>
