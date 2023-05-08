<script>
	// @ts-nocheck

	import CardDetailsForm from './(components)/cardDetailsForm.svelte';
	import CardDetails from './(components)/cardDetails.svelte';
	import FormSuccess from './(components)/formSuccess.svelte';

	let detailsSend = false;

	const handleDetailsSend = (event) => {
		detailsSend = event.detail.valid;
	};
</script>

<aside>
	<div class="card-back">
		<CardDetails orientation={'back'} />
	</div>
	<div class="card-front">
		<CardDetails orientation={'front'} />
	</div>
</aside>

<main>
	<div class="content">
		{#if !detailsSend}
			<CardDetailsForm on:detailsSend={handleDetailsSend} />
		{:else}
			<FormSuccess />
		{/if}
	</div>
</main>

<footer>
	Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
		>Frontend Mentor</a
	>. Coded by <a target="_blank" href="https://www.frontendmentor.io/profile/sutaC">sutaC</a>.
</footer>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500&display=swap');

	:root {
		/* Primary */

		--gradient-lg-active-input-border: linear-gradient(hsl(249, 99%, 64%), hsl(278, 94%, 30%));
		--clr-Red-input-errors: hsl(0, 100%, 66%);

		/* Neutral */

		--clr-White: hsl(0, 0%, 100%);
		--clr-Light-grayish-violet: hsl(270, 3%, 87%);
		--clr-Dark-grayish-violet: hsl(279, 6%, 55%);
		--clr-Very-dark-violet: hsl(278, 68%, 11%);
	}

	:global(body) {
		font-family: 'Space Grotesk', sans-serif;
	}

	* {
		box-sizing: border-box;
	}

	/* Main styles */

	:global(body) {
		margin: 0;
		min-height: 100vh;
		width: 100vw;
	}

	aside {
		background: url('$lib/images/bg-main-mobile.png') no-repeat;
		background-size: cover;

		min-height: 30vh;

		position: relative;
	}

	.card-front {
		position: absolute;
		left: 5%;
		bottom: -30%;
	}

	.card-back {
		position: absolute;
		right: 5%;
		top: 10%;
	}

	main {
		height: 70vh;
		display: flex;
		align-items: center;
		justify-content: end;
		flex-direction: column;
		padding: 3rem 1.5rem;
	}

	/* Desktop view  */

	@media (width >= 1000px) {
		:global(body) {
			display: flex;
		}

		:global(body) > * {
			height: 100%;
		}

		aside {
			width: 30%;
			background: url('$lib/images/bg-main-desktop.png');
		}

		main {
			width: 70%;
		}

		.content {
			max-width: 40%;
		}

		.card-front {
			top: 0;
			right: 0;
			left: 0;
			bottom: 0;

			top: 25%;
			left: 55%;
		}

		.card-back {
			top: 0;
			right: 0;
			left: 0;
			bottom: 0;

			top: 55%;
			left: 70%;
		}
	}

	/* / Main styles */

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
