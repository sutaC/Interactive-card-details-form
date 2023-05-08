<script>
	// @ts-nocheck

	import { createEventDispatcher } from 'svelte';
	import MyButton from './myButton.svelte';

	const dispatch = createEventDispatcher();

	let name, cardNumber, expDateMonth, expDateYear, cvc;
	let errors = [];

	const handleSubmit = () => {
		errors = [];

		// Validation
		if (!name) {
			errors.push({ field: 'name', message: "Can't be blank" });
		}

		if (!cardNumber) {
			errors.push({ field: 'cardNumber', message: "Can't be blank" });
		} else if (!Number(cardNumber) || String(cardNumber).length != 16) {
			errors.push({ field: 'cardNumber', message: 'Wrong format, number only' });
		}

		if (!expDateMonth) {
			errors.push({ field: 'expDateMonth', message: "Can't be blank" });
		} else if (!Number(expDateMonth) || expDateMonth > 12 || expDateMonth < 1) {
			errors.push({ field: 'expDateMonth', message: 'Wrong format, number only' });
		}

		if (!expDateYear) {
			errors.push({ field: 'expDateYear', message: "Can't be blank" });
		} else if (!Number(expDateYear) || Number(expDateYear) < 2023) {
			errors.push({ field: 'expDateYear', message: 'Wrong format, number only' });
		}

		if (!cvc) {
			errors.push({ field: 'cvc', message: "Can't be blank" });
		} else if (!Number(cvc) || String(cvc).length != 3) {
			errors.push({ field: 'cvc', message: 'Wrong format, number only' });
		}

		// Check errors
		let valid = errors.length > 0 ? false : true;
		console.table(errors);

		if (valid) {
			dispatch('detailsSend', {
				valid,
				data: { name, cardNumber, expDateMonth, expDateYear, cvc }
			});
		}
	};
</script>

<form on:submit|preventDefault={handleSubmit}>
	<div>
		<label for="name">Cardholder Name</label>
		<input
			type="text"
			id="name"
			name="name"
			placeholder="e.g. Jane Appleseed"
			bind:value={name}
			class:error-field={errors.filter((err) => err.field === 'name').length > 0}
			minlength="6"
			maxlength="64"
		/>
		{#each errors.filter((err) => err.field === 'name') as err}
			<p class="error-msg">{err.message}</p>
		{/each}
	</div>

	<div>
		<label for="cardNumber">Card Number</label>
		<input
			type="number"
			class="error-field"
			id="cardNumber"
			name="cardNumber"
			placeholder="e.g. 1234 5678 9123 0000"
			bind:value={cardNumber}
			class:error-field={errors.filter((err) => err.field === 'cardNumber').length > 0}
			minlength="16"
			maxlength="16"
		/>
		{#each errors.filter((err) => err.field === 'cardNumber') as err}
			<p class="error-msg">{err.message}</p>
		{/each}
	</div>

	<div class="wrap details">
		<div>
			<label for="expDate">Exp. Date (MM/YY)</label>
			<div class="wrap">
				<input
					type="number"
					id="expDateMonth"
					name="expDateMonth"
					placeholder="MM"
					bind:value={expDateMonth}
					class:error-field={errors.filter((err) => err.field === 'expDateMonth').length > 0}
					min="1"
					max="12"
				/>
				<input
					type="number"
					id="expDateYear"
					name="expDateYear"
					placeholder="YY"
					bind:value={expDateYear}
					class:error-field={errors.filter((err) => err.field === 'expDateYear').length > 0}
					min="2023"
				/>
			</div>
			{#each errors.filter((err) => err.field === 'expDateMonth' || err.field === 'expDateYear') as err}
				<p class="error-msg">{err.message}</p>
			{/each}
		</div>
		<div>
			<label for="cvc">CVC</label>
			<input
				type="number"
				id="cvc"
				name="cvc"
				placeholder="e.g. 123"
				bind:value={cvc}
				class:error-field={errors.filter((err) => err.field === 'cvc').length > 0}
				minlength="3"
				maxlength="3"
			/>
			{#each errors.filter((err) => err.field === 'cvc') as err}
				<p class="error-msg">{err.message}</p>
			{/each}
		</div>
	</div>

	<MyButton>Confirm</MyButton>
</form>

<style>
	input {
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
	input:hover,
	input:focus {
		border: 1px outset hsl(249, 99%, 64%);
	}

	/* Error handling  */

	.error-field {
		border-color: var(--clr-Red-input-errors);
	}
	.error-msg {
		color: var(--clr-Red-input-errors);
		font-size: 0.7rem;
		margin: 0;
	}
</style>
