<script>
	import items from "./items";
	import { cartStore } from "./stores";

	const changeQuantity = (e, item) => {
		const newQuantity = Number(e.target.value);
		cartStore.update((items) => {
			if (newQuantity && !item.quantity) {
				items.push(item);
			} else if (newQuantity === 0 && item.quantity) {
				const [description] = item;
				items = items.filter((i) => i.description !== description);
			}
			item.quantity = newQuantity;

			return items;
		});
	};
</script>

<style>
	input {
		width: 60px;
	}
</style>

<table>
	<thead>
		<tr>
			<th>Description</th>
			<th>Price</th>
			<th>Quantity</th>
		</tr>
	</thead>
	<tbody>
		{#each items as item}
			<tr>
					<td>{item.description}</td>
					<td>${item.price.toFixed(2) }</td>
					<td>
						<input 	
							type="number"
							min='0'
							on:input={e => changeQuantity(e, item)}
							value={item.quantity}
						>
					</td>
			</tr>
		{/each}
	</tbody>
</table>