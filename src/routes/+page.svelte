<aside>
	<div class="card">000</div>
	<div class="card">0000 0000 0000 0000 Jane Appleseed 00/00</div>
</aside>

<main>
	<form>
		<label for="name">Cardholder Name</label>
		<input type="text" id="name" name="name" placeholder="e.g. Jane Appleseed" />

		<label for="cardNumber">Card Number</label>
		<input type="number" id="cardNumber" name="cardNumber" placeholder="e.g. 1234 5678 9123 0000" />

		<label for="expDate">Exp. Date (MM/YY)</label>
		<input type="number" id="expDate" name="expDateMonth" placeholder="MM" />
		<input type="number" id="expDate" name="expDateYear" placeholder="YY" />

		<label for="cvc">CVC</label>
		<input type="number" id="cvc" name="cvc" placeholder="e.g. 123" />

		<button>Confirm</button>
	</form>

	<!-- Completed state -->

	{#if false}
		Thank you! We've added your card details Continue
	{/if}
</main>

<footer>
	Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
		>Frontend Mentor</a
	>. Coded by <a target="_blank" href="https://www.frontendmentor.io/profile/sutaC">sutaC</a>.
</footer>

<style>
	footer {
		width: 100%;
		position: fixed;
		left: 0;
		bottom: 0;
		text-align: center;
		font-size: 10px;
		mix-blend-mode: difference;
	}
</style>
