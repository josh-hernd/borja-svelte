<script lang="ts">
	import Content from '$lib/the-content/content';
	import Head from '$lib/components/head/head.svelte';
import ColSection from '$lib/components/sections/colSection.svelte';
import ImaGrid from '$lib/components/image-grids/imaGrid.svelte';
</script>

<Head
	postTitle={Content.AboutPage.title}
	postDesc={Content.AboutPage.description}
	postKeywords={Content.AboutPage.keywords}
	siteUrl={Content.AboutPage.site_url}
	postOgImg={Content.AboutPage.og_image}
/>
<ColSection 
	headline={Content.AboutPage.postAbout.headline}
	parag={Content.AboutPage.postAbout.paragraph}
	serviceList={undefined}
	buttonEl={undefined}
	imgSrc={Content.AboutPage.postAbout.image}
	secStyle={{color: 'none', padding: '80px 0 40px', marging: 'auto' }}
/>
<ImaGrid 
	gridArray={Content.AboutPage.postGrid}
/>