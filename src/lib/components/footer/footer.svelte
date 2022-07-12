<script lang="ts">
import ColSection from "../sections/colSection.svelte";

    interface preFoot {
        headline: string;
        button: {url: string; title: string};
        image: {src: string; alt: string }
    }

    export let preFooter: preFoot;

	interface foot {
		logo: { src: string; url: string; alt: string };
		items: { id: number; label: string; url: string; type: string }[];
		socialMedia: { channel: { ref: string; icon: string; }; }[]
	}

	export let footerData: foot;
</script>

<ColSection 
	headline={preFooter.headline}
	parag={undefined}
	serviceList={undefined}
	buttonEl={preFooter.button}
	imgSrc={preFooter.image}
	secStyle={{color: 'rgb(198, 16, 16)', padding: '0'}}
/>
<footer>
	<div class="wrap">
		<div class="se">
			<a href={footerData.logo.url}><img src={footerData.logo.src} alt={footerData.logo.alt} /></a
			>
		</div>
		<div class="se">
			<ul class="ftNav">
				{#each footerData.items as item}
					<li><a href={item.url}>{item.label}</a></li>
				{/each}
			</ul>
		</div>
        <div class="se">
            <ul>
            {#each footerData.socialMedia as media}
                <li><a href="{media.channel.ref}" target="_blank" rel="noopener noreferrer"><i class={media.channel.icon}/></a></li>
            {/each}
        </ul>
        </div>
	</div>
</footer>

<style lang="sass">
footer
    text-align: center
    padding: 40px 0
    img
        width: 100%
        max-width: 265px

.se
    padding: 10px 0

ul
    display: flex
    justify-content: center
    padding: 5px 0
    margin: 0
    li
        margin: 0 10px
        i
           font-size: 35px

</style>
