<script lang="ts">
import Blurb from "./blurb.svelte";

export let headline: string;

interface blurbsItem {
    icon?: string | undefined;
    title?: string | undefined;
    paragraph?: string | undefined;
}
export let blurbItems: blurbsItem [];
</script>

<div class="blurbSec">
    <h3>{headline}</h3>
    <div class="treeCol">
        {#each blurbItems as blurbItem}
            <Blurb 
            icon={blurbItem.icon}
            title={blurbItem.title}
            parag={blurbItem.paragraph}
            />
        {/each}
    </div>
</div>

<style lang="sass">
@use '../../../abstract/breakPoints' as *
.blurbSec
    width: calc( 100% - 40px )   
    padding: 60px 20px
    background: #F6F6F6
    h3
        font-size: 30px
        color: #232222
        text-align: center

.treeCol
    width: 80%
    margin: auto
    display: flex
    justify-content: center   
    @include dynamicPoints($min: 200px, $max: 960px)
        width: 100%
        flex-direction: column
</style>