<script lang="ts">
export let label: string | undefined;
export let icon:string | undefined;
export let fontColor: string | undefined;
export let labelColor: string | undefined;
</script>

<div class="labelWrap" style="--labelColor: {labelColor};">
    <img src={icon} alt="icon" srcset="" width="19">
    <span style="--labelFont: {fontColor};">{label}</span>
</div>

<style lang="sass">
.labelWrap
    --labelColor: #C61010
    background: var(--labelColor)
    padding: 10px 15px
    margin: 5px
    display: inline-flex
    justify-content: center
    align-items: center
    border-radius: 3px
    box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.1)
    img
        margin-right: 9px 
    span
        --labelFont: #fff
        color: var(--labelFont)
        font-family: 'Exo 2'
        font-style: normal
        font-weight: 600
        font-size: 16px
        line-height: 19px
        text-transform: uppercase
</style>