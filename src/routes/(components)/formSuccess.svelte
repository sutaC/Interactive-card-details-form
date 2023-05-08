<script>
	import MyButton from './myButton.svelte';
</script>

<section>
	<div class="icon-complete" />

	<div>
		<h1>Thank you!</h1>
		<p>We've added your card details</p>
	</div>

	<MyButton>Continue</MyButton>
</section>

<style>
	section {
		height: 90%;
		width: 100%;
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		flex-direction: column;
		text-align: center;
	}

	section > * {
		width: 100%;
	}

	.icon-complete {
		background: url('$lib/images/icon-complete.svg');
		background-size: contain;
		background-repeat: no-repeat;
		background-position: center;

		--size: 5rem;
		height: var(--size);
		width: var(--size);
	}

	h1 {
		text-transform: uppercase;
		font-size: 2rem;
		letter-spacing: 0.3rem;
		margin: 2rem 0 0.5rem 0;
	}

	p {
		color: var(--clr-Dark-grayish-violet);
		font-size: 1.1rem;
		margin: 0.5rem 0 2rem 0;
	}
</style>
