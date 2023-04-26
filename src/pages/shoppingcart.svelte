<script>
	import Title from "../components/Title.svelte";
    import "./../css/shoppingcart.css";
	let cartItems=localStorage.getItem("cartItems");
	let items=cartItems ? JSON.parse(cartItems) : [];
</script>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>cart</title>
</head>
<body>
    <Title/>
    <h1>Shopping Cart</h1>
	<table>
		<thead>
			<tr>
				<th>Product</th>
				<th>Price</th>
				<th>Quantity</th>
				<th>Total</th>
			</tr>
		</thead>
		<tbody>
			{#each items as item}
				<tr>
					<td>{item.name}</td>
					<td>${item.discount_price || item.price}</td>
					<td><input type="number" min="0" value={item.quantity}></td>
					<td>${item.quantity * (item.discount_price || item.price)}</td>
				</tr>
			{/each}
		</tbody>
        <tfoot>
            <tr>
              <td colspan="3">Shipping:</td>
              <td>$5.00</td>
            </tr>
            <tr>
              <td colspan="3">Total:</td>
              <td>$50.00</td>
            </tr>
          </tfoot>
	</table>
	<h2>Shipping Information</h2>
	<form>
		<label for="name">Name:</label>
		<input type="text" id="name" name="name" placeholder="Enter Your Name" required><br>
		<label for="phone">Phone:</label>
		<input type="text" id="phone" name="phone" required><br>
		<label for="email">Email:</label>
		<input type="text" id="email" name="email" placeholder="user@gmail.com"><br>
		<label for="address">Address:</label>
		<input type="text" id="address" name="address" required><br>
		<label for="shipping">Shipping Option:</label>
		<select id="shipping" name="shipping">
			<option value="parcel">Parcel Service</option>
		</select>
	</form>
	<h2>Payment Information</h2>
	<form>
		<label for="payment">Payment Option:</label>
		<select id="payment" name="payment">
			<option value="cash">Cash on Demand</option>
		</select>
	</form>
	<button>Place Order</button>

    
</body>