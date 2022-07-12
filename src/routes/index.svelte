<script lang="ts">
	import Content from '$lib/the-content/content';
	import Head from '$lib/components/head/head.svelte';
	import FullSection from '$lib/components/sections/fullSection.svelte';
	import SimpleSection from '$lib/components/sections/simpleSection.svelte';
	import BlurbSection from '$lib/components/sections/blurb-section/blurbSection.svelte';
	import ColSection from '$lib/components/sections/colSection.svelte';
	import ImaGrid from '$lib/components/image-grids/imaGrid.svelte';
</script>

<Head
	postTitle={Content.HomePage.title}
	postDesc={Content.HomePage.description}
	postKeywords={Content.HomePage.keywords}
	siteUrl={Content.HomePage.site_url}
	postOgImg={Content.HomePage.og_image}
/>

<FullSection
	logo={Content.HomePage.full_sec.logo.src}
	altLogo={Content.HomePage.full_sec.logo.alt}
	title={Content.HomePage.full_sec.title}
	backgroundImg={Content.HomePage.full_sec.background_img}
/>

<SimpleSection
	headline={Content.HomePage.postIntro.headline}
	parag={Content.HomePage.postIntro.paragraph}
	reasonBadge={[]}
	button={{}}
/>

<BlurbSection
	headline={Content.HomePage.postBlurbs.headline}
	blurbItems={Content.HomePage.postBlurbs.blurbs}
/>

<ColSection
	headline={Content.HomePage.postService.headline}
	parag={Content.HomePage.postService.paragraph}
	serviceList={Content.HomePage.postService.services}
	buttonEl={Content.HomePage.postService.button}
	imgSrc={Content.HomePage.postService.image}
	secStyle={{color: 'rgb(198, 16, 16)', padding: '0', marging: 'auto' }}
/>

<SimpleSection
	headline={Content.HomePage.postArg.headline}
	parag={Content.HomePage.postArg.paragraph}
	reasonBadge={Content.HomePage.postArg.reasons}
	button={Content.HomePage.postArg.button}
/>

<ImaGrid gridArray={Content.HomePage.postGrid} />

