<script lang="ts">
	export let url: string | undefined;
	export let title: string | undefined;
	export let fontColor: string;
	export let backgroundColor: string;

	export let positon: string;

	function buttonAlign(align: string) {
		if (align === 'left') {
			return 'margin-right: auto;';
		} else if (align === 'right') {
			return 'margin-left: auto;';
		} else if (align === 'center' || align === 'default') {
			return 'margin: auto;';
		} else {
			return 'margin: auto;';
		}
	}
</script>

<div class="btnWrap" style={buttonAlign(positon)}>
	<a href={url} style="--btnBcolor: {backgroundColor};">
		<span style="--btnFont: {fontColor};">{title}</span>
	</a>
</div>

<style lang="sass">
.btnWrap
    width: max-content
    box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.1)
a
    --btnBcolor: #000
    background: var(--btnBcolor)
    padding: 10px 15px
    border-radius: 3px
    display: block
    text-decoration: none
    span
        --btnFont: #fff
        color: var(--btnFont)
        font-family: 'Exo 2'
        font-style: normal
        font-weight: 600
        font-size: 16px
        line-height: 19px
        text-transform: uppercase

</style>
