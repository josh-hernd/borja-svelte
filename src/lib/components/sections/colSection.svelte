<script lang="ts">
	import SimpleButton from '../buttons/simpleButton.svelte';

	export let headline: string | undefined;
	export let parag: string | undefined;
	export let serviceList: ArrayLike<unknown> | undefined;

	interface btnElem {
		url?: string;
		title?: string;
	}
	export let buttonEl: btnElem | undefined;

	interface imgElem {
		src?: string;
		alt?: string;
	}
	export let imgSrc: imgElem;


	interface styleInt {
		color?: string | undefined;
		padding?: string;
		marging?: string;
	}

	export let secStyle: styleInt = {
		padding: '0',
		marging: '0px'
	};
</script>

<div class="colSec" style="padding: {secStyle.padding}; --marg: {secStyle.marging}; background:{secStyle.color};">
	<div class="twoCol">
		<div class="leftCol">
			<div class="headline">
				<h3 class:dark={secStyle.color === 'none' || secStyle.color === '#E5E5E5'}>{@html headline}</h3>
				{#if parag != undefined}
					<p class:dark={secStyle.color === 'none' || secStyle.color === '#E5E5E5'}>{@html parag}</p>
				{/if}
			</div>
			<div class="listDisplay">
				{#if serviceList != undefined}
					<ul>
						{#each serviceList as list}
							<li  class:dark={secStyle.color === 'none' || secStyle.color === '#E5E5E5'}>
								<img
									src="/jpeg/home-page/icons/check.svg"
									alt="check icon"
									srcset=""
									width="11px"
								/>
								{@html list}
							</li>
						{/each}
					</ul>
				{/if}
			</div>
			{#if buttonEl != undefined}
				<SimpleButton
					url={buttonEl.url}
					title={buttonEl.title}
					fontColor="#C61010"
					backgroundColor="#fff"
					positon="left"
				/>
			{/if}
		</div>
		<div class="rightCol">
			<div class="imgWrap">
				<img src={imgSrc.src} alt={imgSrc.alt} srcset="" />
			</div>
		</div>
	</div>
</div>

<style lang="sass">
@use '../../abstract/breakPoints' as *

h3
    width: 75%
    line-height: 1.2em

h3, p, li
    color: #fff
.dark
    color: #000

.colSec
    --marg: 0
    margin: var(--marg)

.twoCol
    display: flex
    justify-content: space-between
    align-items: center
    @include dynamicPoints($min: 200px, $max: 960px)
        flex-direction: column
        .headline
            text-align: center
            h3
                width: 100%
                margin: auto
.leftCol
    width: 50%
    margin: auto
    @include dynamicPoints($min: 200px, $max: 960px)
        width: 80%
        margin: 40px auto

.listDisplay
    margin-bottom: 30px
    ul
        display: flex
        flex-wrap: wrap
        li
            width: 50%
            margin: 5px 0
            img
                margin-right: 5px
    @include dynamicPoints($min: 200px, $max: 960px)
        ul
            flex-direction: column
            li
                width: 100%
.rightCol
    .imgWrap
        width: 100%
        max-width: 542px
    img
        width: 100%
        display: block
</style>
