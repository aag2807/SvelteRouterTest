<script>
	import { cartStore } from "./stores";

	let total = $cartStore.reduce((acc, item) => acc + item.price * item.quantity, 0);

	let city = '';
	let name = '';
	let state = '';
	let street = '';
	let zip = '';

	$: shipping = total === 0 ? 0 : total < 10 ? 2 : total < 30 ? 6 : 10; 

	const format = cost => '$' + cost.toFixed(2);
</script>

<style>
	
	form {
		display: inline-block;
	}

	form > label {
		display: block;
		margin-bottom: 5px;
		text-align: right;
		width: 100%;
	}

	.totals {
		margin-top: 10px;
	}
</style>

<h1>Ship</h1>

<form on:submit|preventDefault>
	<label>
		Name
		<input type="text" bind:value={name}>
	</label>
	<label>
		Street 
		<input type="text" bind:value={street}>
	</label>
	<label>
		City 
		<input type="text" bind:value={city}>
	</label>
	<label>
		State 
		<input type="text" bind:value={state}>
	</label>
	<label>
		Zip 
		<input type="text" bind:value={zip}>
	</label>
</form>

<h3>Shipping to:</h3>
<div>{name}</div>
<div>{street}</div>
<div>{city ? city + ',' : '' } {state} {zip}</div>

<div class="totals">
	<label>Total: {format(total)}</label> 
	<label>Shipping: {format(shipping)}</label> 
	<label>Grand Total: {format(total + shipping)}</label> 
</div>