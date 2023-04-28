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
<img src={product.media.edges[0].node.image.url} alt=""/>
<p class="id">ID: {product.id}</p>
<h2>{product.title}</h2>
<p class="description">{product.description}</p>
<p class="price">
  Price:$<span class="sale-price">{product.variants.edges[0].node.price.amount}</span>
</p>
<button class="add-to-cart" on:click={handleAddToCart}>Add to Cart</button>