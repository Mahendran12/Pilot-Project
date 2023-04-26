<script>
    import TitleBar from "../components/TitleBar.svelte";
    import "./../css/homepage.css";
    import ProductCard from "../components/ProductCard.svelte";
    import products from './../mockdata/products.json';
    import Content from "../components/Content.svelte";
    let specialProducts = products.filter((product) => product.is_special_product);
</script>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
</head>
<body>
<TitleBar/>
    <Content/>
    <div class="c-image">
        <img src="https://sslimages.shoppersstop.com/sys-master/root/h74/hf5/29868030459934/veromoda-only_Top-Banner-Web_womens%20page_main%20banner_200423.jpg" alt="Advertisement">
    </div>
    <div>
        <h2 class="sp">Special Products</h2>
        <main>
            <ul class="product-list">
              {#each specialProducts as product}
				<li class="itachi">
					<ProductCard product={product} />
				</li>
			  {/each}
            </ul>
        </main>
    </div>  
</body>