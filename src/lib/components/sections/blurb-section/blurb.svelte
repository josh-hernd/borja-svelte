<script lang="ts">
export let icon: string | undefined;
export let title: string | undefined;
export let parag: string | undefined;
</script>

<div class="blurb">
    <img src="{icon}" alt="icon" srcset="">
    <h3>{title}</h3>
    <p>{parag}</p>
</div>

<style lang="sass">
@use '../../../abstract/breakPoints' as *
.blurb
    width: calc( 100% - 50px )
    padding: 40px 25px
    margin: 12.5px
    background: #fff
    text-align: center
    border-radius: 3px
    box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.1)
    img
        border-radius: 100%
        box-shadow: 0px 0px 5px 3px rgba(0, 0, 0, 0.15)
    h3
        font-size: 20px
    @include dynamicPoints($min: 200px, $max: 960px)
        margin: 12.5px 0
        h3, p
            margin: 0 auto

</style>