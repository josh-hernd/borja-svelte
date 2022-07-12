<script>
	import Content from '$lib/the-content/content';
	import Head from '$lib/components/head/head.svelte';
	import ImaGrid from '$lib/components/image-grids/imaGrid.svelte';
	import ColSection from '$lib/components/sections/colSection.svelte';
	import SimpleSection from '$lib/components/sections/simpleSection.svelte';
</script>

<Head
	postTitle={Content.ServicePage.title}
	postDesc={Content.ServicePage.description}
	postKeywords={Content.ServicePage.keywords}
	siteUrl={Content.ServicePage.site_url}
	postOgImg={Content.ServicePage.og_image}
/>

<SimpleSection
	headline={Content.ServicePage.postIntro.headline}
	parag={undefined}
	reasonBadge={undefined}
	button={{}}
/>

{#each Content.ServicePage.postService as serv}
	<ColSection
		headline={serv.headline}
		parag={serv.paragraph}
		serviceList={serv.services}
		buttonEl={undefined}
		imgSrc={serv.image}
		secStyle={{ color: serv.styleBground, padding: '60px 0', marging: '0 0 60px' }}
	/>
{/each}

<SimpleSection
	headline={Content.ServicePage.projects.headline}
	parag={Content.ServicePage.projects.paragraph}
	reasonBadge={undefined}
	button={{}}
/>

<ImaGrid gridArray={Content.ServicePage.postGrid} />
