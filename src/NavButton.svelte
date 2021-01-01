<script>
	export let name;
	export let pageName;
</script>

<style>
	button {
		--space: 0.5rem;

		background-color: #fff;
		border-radius: var(--space);
		height: 38px;
		margin-right: var(--space);
		padding: var(--space);
	}

	.active {
		background-color: orange;
	}

</style>

<button
	class:active={pageName === name}
	on:click={() => pageName = name}
>
	<slot />
</button>

