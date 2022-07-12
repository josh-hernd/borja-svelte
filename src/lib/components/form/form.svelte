<script lang="ts">
	interface Form {
		label?: string | undefined | null;
		type?: string | undefined | null;
		name?: string | undefined | null;
		id?: string | undefined | null;
		placehold?: string | undefined | null;
	}

	export let buildForm: Form[];

	let success = false;
	let messages: string;
	const handleSubmit = async (e: SubmitEvent) => {
		const formData = new FormData(e.target as HTMLFormElement);
		const data = Object.fromEntries(formData);
		console.log(data);
		
		const Timeout = (time: number) => {
			let controller = new AbortController();
			setTimeout(() => controller.abort(), time * 1000);
			return controller;
		};
		// Catch Bots
		if (!data.honey) {
			const res = await fetch(`http://0.0.0.0:3000/`, {
				signal: Timeout(5).signal,
				method: 'POST',
				headers: {
					'Content-type': 'application/json'
				},
				mode: 'cors',
				body: JSON.stringify(data)
			})
				.then((res) => {
					if (!res.ok) {
						messages = 'Sorry we are having issues sending your message.';
						success = true;
						throw new Error('Network response was not OK');
					}
					return res;
				})
				.then((res) => {
					messages = 'Message was sent!';
					success = true;
				})
				.catch((error) => {
					messages = 'Sorry we are having issues sending your message.';
					success = true;
					console.log(error);
					
				});
		} else {
			messages = 'Sorry! Spam messages are not accepted.';
			success = true;
		}
	};
</script>

<form on:submit|preventDefault={handleSubmit}>
	<div class="wrap">
		{#each buildForm as inputs}
			{#if inputs.name !== 'comments'}
				<div class="wrapInput">
					<label for="clientName">{inputs.label}</label>
					<input
						type={inputs.type}
						name={inputs.name}
						id={inputs.id}
						placeholder={inputs.placehold}
						required
					/>
				</div>
			{:else}
				<div class="wrapInput full">
					<label for="clientName">{inputs.label}</label>
					<textarea
						name={inputs.name}
						id={inputs.id}
						placeholder={inputs.placehold}
						cols="30"
						rows="10"
					/>
				</div>
			{/if}
		{/each}
		<div class="bzzz" style="display: none;">
			<label for="honey">For the bees!</label>
			<input type="text" name="honey" id="pot" />
		</div>
		<div class="wrapInput submitWrap">
			<input type="submit" value="Send" id="submit" disabled={success}/>
			{#if messages}
				<p>{messages}</p>
			{/if}
		</div>
	</div>
</form>

<style lang="sass">
@use '../../abstract/breakPoints' as *

form
    padding: 40px
    background: #F6F6F6

.wrap
    display: flex
    flex-wrap: wrap
.wrapInput
    width: calc( 50% - 40px )
    margin: 10px 20px
    display: flex
    flex-direction: column
    @include dynamicPoints($min: 200px, $max: 960px)
        width: calc( 100% - 40px )

.full
    width: calc( 100% - 40px )

label
    font-size: 19px
    margin-bottom: 5px

input, textarea
    background: #fff
    padding: 10px 15px
    border-color: rgba(0, 0, 0, 0.1)
    box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.01)


input#submit
    -webkit-appearance: none
    -moz-appearance: none
    width: max-content
    box-shadow: 0px 0px 7px 3px rgba(0, 0, 0, 0.1)
    --btnBcolor: #c61010
    background: var(--btnBcolor)
    padding: 10px 15px
    border-radius: 3px
    border: none
    --btnFont: #fff
    color: var(--btnFont)
    font-family: 'Exo 2'
    font-style: normal
    font-weight: 600
    font-size: 16px
    line-height: 19px
    text-transform: uppercase
    &:disabled
        --btnBcolor: #c6101080
.submitWrap
    flex-direction: row
    align-items: center
    p
        margin-left: 20px
</style>
