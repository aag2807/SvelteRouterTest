<script>
	import { cartStore } from "./stores";

	import NavButton from "./NavButton.svelte";
	import Cart from "./Cart.svelte";
	import Ship from "./Ship.svelte";
	import Shop from "./Shop.svelte";

	const pageMap = {
		cart: Cart,
		ship: Ship,
		shop: Shop,
	};
	let pageName = "shop";
</script>

<style>
	main {
		padding: 1em;
	}

	nav {
		display: flex;
		align-items: center;
		background-color: cornflowerblue;
		padding: 10px;
	}
</style>


<nav>
	<NavButton bind:pageName name='shop'>Shop</NavButton>
	<NavButton bind:pageName name='cart'>
		&#x1F6D2; {$cartStore.length}
	</NavButton>
	<NavButton bind:pageName name='ship'>Ship</NavButton>
</nav>

<main>
	<svelte:component this={pageMap[pageName]} />
</main>
