<button on:click><slot /></button>

<style>
	button {
		background-color: var(--clr-Very-dark-violet);
		border: none;
		color: var(--clr-White);
		padding: 0.8rem;
		font-size: 1rem;
		border-radius: 0.5rem;
		margin: 0;
		width: 100%;
		font-family: 'Space Grotesk', sans-serif;
	}
	:active {
		opacity: 0.8;
	}
</style>
