<script lang="ts">
interface gridSrc {
    src?: string;
    alt?: string;
}

export let gridArray: gridSrc [];
</script>

<div class="imaGrid">
    {#each gridArray as imgSrc }
        <div class="imageWrap">
            <img src={imgSrc.src} alt={imgSrc.alt} srcset="">
        </div>
    {/each}
    
</div>

<style lang="sass">
@use '../../abstract/breakPoints' as *
.imaGrid
    display: flex
    flex-wrap: wrap
    .imageWrap
        width: 50%
        position: relative
        img
            width: calc(100% - 20px)
            margin: 10px
            box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.1)
            display: block
    @include dynamicPoints($min: 200px, $max: 1025px)
        flex-direction: column
        .imageWrap
            width: 100%
</style>