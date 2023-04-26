<script>
  export let product;
  let handleAddToCart = ()=>{
    const existingItems=localStorage.getItem("cartItems");
    let cartItems = existingItems ? JSON.parse(existingItems) : [];
    const itemIndex=cartItems.findIndex(i=>i.id===product.id);
    if(cartItems.length && itemIndex >= 0){
      cartItems[itemIndex].quantity += 1;
    }else{
      cartItems.push({
        ...product,
        quantity: 1
      });
    }
    localStorage.setItem("cartItems",JSON.stringify(cartItems));
  };
</script>

<img src={product.image_url} alt="Color linen saree with zari border"/>
<p class="id">ID: {product.id}</p>
<h2>{product.name}</h2>
<p class="description">{product.description}</p>
<p class="price">
  Price: $<s>{product.price}</s> $<span class="sale-price">{product.discount_price}</span>
</p>
<p class="discount">
  Discount: <span class="discount-percentage">{product.discount_percentage}</span>
</p>
<button class="add-to-cart" on:click={handleAddToCart}>Add to Cart</button>