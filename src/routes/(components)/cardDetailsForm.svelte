<form>
	<div>
		<label for="name">Cardholder Name</label>
		<input type="text" id="name" name="name" placeholder="e.g. Jane Appleseed" />
	</div>

	<div>
		<label for="cardNumber">Card Number</label>
		<input type="number" id="cardNumber" name="cardNumber" placeholder="e.g. 1234 5678 9123 0000" />
	</div>

	<div class="wrap details">
		<div>
			<label for="expDate">Exp. Date (MM/YY)</label>
			<div class="wrap">
				<input type="number" id="expDateMonth" name="expDateMonth" placeholder="MM" />
				<input type="number" id="expDateYear" name="expDateYear" placeholder="YY" />
			</div>
		</div>
		<div>
			<label for="cvc">CVC</label>
			<input type="number" id="cvc" name="cvc" placeholder="e.g. 123" />
		</div>
	</div>

	<button>Confirm</button>
</form>

<style>
	input,
	button {
		font-family: 'Space Grotesk', sans-serif;
	}

	.wrap {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 0.5rem;
	}

	form > * {
		margin: 1.4rem 0;
		width: 100%;
	}

	.details > div {
		width: 50%;
	}

	form :is(label, input) {
		width: 100%;
		margin: 0.25rem 0;
	}

	label {
		text-transform: uppercase;
		font-size: 0.8rem;
	}

	input {
		display: block;
		border: 1px solid var(--clr-Light-grayish-violet);
		padding: 0.6rem;
		border-radius: 0.5rem;
	}
	::placeholder {
		color: var(--clr-Dark-grayish-violet);
	}

	button {
		background-color: var(--clr-Very-dark-violet);
		border: none;
		color: var(--clr-White);
		padding: 0.8rem;
		font-size: 1rem;
		border-radius: 0.5rem;
		margin: 0;
	}
</style>
