<script lang="ts">
export let logo: string;
export let altLogo: string;
export let title: string;
export let backgroundImg: string;
</script>

<div class="fullWrap" style="background-image: url({backgroundImg});">
    <div class="centered">
        <img src={logo} alt={altLogo} >
        <h3>{title}</h3>
    </div>
</div>

<style lang="sass">
@use '../../abstract/breakPoints' as *

.fullWrap
    width: calc(100% - 40px)
    height: 100vh
    padding: 20px
    background-size: cover
    background-position: center
    display: flex
    justify-content: center
    align-items: center

.centered
    text-align: center   
    img
        width: 100%
        max-width: 360px 
        -webkit-filter: drop-shadow( 0px 0px 5px rgba(225, 225, 225, 0.35))
        filter: drop-shadow( 0px 0px 5px rgba(225, 225, 225, 0.35))
h3 
    font-size: 61px
    color: #FFFFFF
    padding-bottom: 7px
    border-bottom: solid 1px #fff
    text-shadow: 0px 0px 10px rgb(225 225 225 / 35%)
    @include dynamicPoints($min: 200px,$max: 729px)
        font-size: 35px
    
</style>