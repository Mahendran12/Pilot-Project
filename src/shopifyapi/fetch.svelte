<script>
    import { json } from "@sveltejs/kit";

    let products = [];
  
    async function fetchProducts() {
      const shopifyApiKey = 'df0d72fa1af46843a6f1101b6c65eec4';
      const shopifyPassword = 'ff4d14a3ddc94a14b65b4afbf26cf518';
      const shopifyEndpoint = 'https://maheshop-7143.myshopify.com/api/2023-04/graphql.json';
      let variables = {
           id: 8328948023597 
                 };
      const requestBody = JSON.stringify({
                        query: `query products {products(first:10){ edges {
                                         cursor
                                          node {
                                            id
                                            title
}
}}
}`
                                  });
      const accessToken = 'cab5b14c2549885be827c94f194f88d5';                    
      
      const response = await fetch(shopifyEndpoint, {
        method: 'POST', 
        body: requestBody,  
      headers: {
       'Content-Type': 'application/json',
       "X-Shopify-Storefront-Access-Token": "cab5b14c2549885be827c94f194f88d5"
        // 'Authorization': `Basic ${btoa(`${shopifyApiKey}:${shopifyPassword}:${accessToken}`)}`
                }
            });

      const data = await response.json();
      console.log(data)
      products = data.data.products.edges;
    }
  </script>
  
  <button on:click={fetchProducts}>Fetch Products</button>

  {#if products.length > 0}
    <ul>
      {#each products as product}
        <li>{product.node.title}</li>
      {/each}
    </ul>
  {:else}
    <p>No products found.</p>
  {/if}
  