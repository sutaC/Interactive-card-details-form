<script>
	export let name = 'Jane Appleseed';
	export let cardNumber = '0000 0000 0000 0000';
	export let expDateMonth = '00';
	export let expDateYear = '00';
	export let cvc = '000';

	export let orientation = 'front';
</script>

<div class="card" class:front={orientation === 'front'} class:back={orientation === 'back'}>
	{#if orientation === 'front'}
		<div class="logo" />
		<div class="details">
			<p class="cardNumber">{cardNumber}</p>
			<div class="wrap">
				<p class="name">{name}</p>
				<p class="expDate">{expDateMonth}/{expDateYear}</p>
			</div>
		</div>
	{:else if orientation === 'back'}
		<p class="cvc">{cvc}</p>
	{:else}
		<p>No valid orientation provided</p>
	{/if}
</div>

<style>
	/* General styles */

	.card {
		margin: 0;

		width: clamp(50vw, 30rem, 75vw);
		height: clamp(15vh, 20rem, 22vh);
	}

	p {
		margin: 0;
	}

	/* Back card design  */

	.back {
		background: url('$lib/images/bg-card-back.png');
		background-size: contain;
		background-repeat: no-repeat;
		position: relative;
	}

	.cvc {
		position: absolute;
		right: 12%;
		top: 49%;
		transform: translate(-50%, -50%);

		font-size: 0.7rem;
		letter-spacing: 0.1rem;
		color: var(--clr-White);
	}

	/* Front card design  */

	.front {
		background: url('$lib/images/bg-card-front.png');
		background-size: contain;
		background-repeat: no-repeat;
		padding: 1rem;
		box-sizing: border-box;

		display: flex;
		justify-content: space-between;
		flex-direction: column;

		color: var(--clr-White);
	}

	.logo {
		background: url('$lib/images/card-logo.svg');
		background-size: contain;
		background-repeat: no-repeat;
		width: 100%;
		height: 25%;
	}

	.cardNumber {
		font-size: 1.1rem;
		letter-spacing: 0.15rem;
		margin: 0.7rem 0;
	}

	.wrap {
		width: 95%;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.name,
	.expDate {
		text-transform: uppercase;
		font-size: 0.6rem;
	}
</style>
