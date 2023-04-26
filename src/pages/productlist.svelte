<script>
    import TitleBar from "../components/TitleBar.svelte";
    import ProductCard from "../components/ProductCard.svelte";
    import "./../css/productlist.css";
    import products from './../mockdata/products.json';
    import Content from "../components/Content.svelte";


</script>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product List</title>
</head>
<body>
    <TitleBar/>
    <Content/>
    <div>
        <h2 class="sp">Shop By Accessory</h2>
        <main>
            <ul class="product-list">
              {#each products as product}
                <li class="naruto">
                  <ProductCard product={product} />
                </li>
              {/each}
            </ul>

          </main>
    </div>  
</body>