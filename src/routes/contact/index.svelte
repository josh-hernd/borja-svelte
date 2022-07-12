<script>
	import Content from '$lib/the-content/content';
	import Form from '$lib/components/form/form.svelte';
	import SimpleSection from '$lib/components/sections/simpleSection.svelte';
</script>

<SimpleSection
	headline={Content.ContactPage.postIntro.headline}
	parag={undefined}
	reasonBadge={[]}
	button={{}}
/>
<div class="wrap">
	<div class="cols">
		<Form buildForm={Content.ContactPage.useForm} />
	</div>
	<div class="cols">
            <div class="inf">
                <div class="logo">
                    <img src="/svg/logo-red.svg" alt="logo" srcset="">
                </div>
                {#each Content.ContactPage.info as inf }
                    <h3><a href={inf.href} target={inf.target ? "_blank" : "_self"}>{inf.title}</a></h3>
                {/each}
                <ul>
                {#each Content.ContactPage.socialMedia as media}
                <li><a href="{media.channel.ref}" target="_blank" rel="noopener noreferrer"><i class={media.channel.icon}/></a></li>
                {/each}
            </ul>
            </div>
    </div>
</div>

<style lang="sass">
@use "../../lib/abstract/breakPoints" as *
h3
    line-height: 1.2em
a
    text-decoration: none
    color: #000
.wrap
    width: 90%
    margin: 10px auto 60px
    display: flex
    .cols
        width: 50%
    .inf
        padding: 40px
    .logo
        width: 100%
        max-width: 221px
        img
            width: 100%
            display: block

    ul
        display: flex
        padding: 5px 0
        margin: 0
        li
            margin: 0 10px
            i
                color: #C61010
                font-size: 35px
    @include dynamicPoints($min: 200px, $max: 960px)
        flex-wrap: wrap
        .cols
            width: 100%
        .logo, h3
            text-align: center
            margin: auto
        h3
            margin: 5px 0
        .inf ul
            justify-content: center
</style>