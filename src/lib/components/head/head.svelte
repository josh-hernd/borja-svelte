<script lang="ts">
export let postTitle: string;
export let postDesc: string;
export let postKeywords: string;
export let siteUrl: string;
export let postOgImg: string;
</script>
<svelte:head>
    <slot>

    <title>{postTitle}</title>
	<meta name="description" content={postDesc} />
	<meta name="keywords" content={postKeywords} />
	<meta property="og:type" content={postTitle} />
	<meta property="og:title" content={postTitle} />
	<meta property="og:description" content={postDesc} />
	<meta property="og:url" content={siteUrl} />
	<meta property="og:image" content={postOgImg} />
	<meta name="twitter:description" content={postDesc} />
    </slot>
</svelte:head>