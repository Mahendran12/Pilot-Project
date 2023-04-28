<script>
    import TitleBar from "../components/TitleBar.svelte";
    import ProductCard from "../components/ProductCard.svelte";
    import "./../css/productlist.css";
    //import products from './../mockdata/products.json';
    import Content from "../components/Content.svelte";
    import Fetch from "../shopifyapi/fetch.svelte";
    export let products=[];
    async function fetchProducts() {
      const shopifyApiKey = 'df0d72fa1af46843a6f1101b6c65eec4';
      const shopifyPassword = 'ff4d14a3ddc94a14b65b4afbf26cf518';
      const shopifyEndpoint = 'https://maheshop-7143.myshopify.com/api/2023-04/graphql.json';
      let variables = {
           id: 8328948023597 
                 };
                 const requestBody = JSON.stringify({
                        query: `query products {
                          products(first:10){ edges {
                              cursor
                                node {
                                  id
                                  title
                                  description
                                  variants(first: 10) {
                                      edges {
                                        cursor
                                        node {
                                          id
                                          title
                                          price {
                                            amount
                                            currencyCode
                                          }
                                        }
                                      }
                                    }
                                  media(first: 10) {
                                  edges {
                                    node {
                                      mediaContentType
                                      alt
                                      ...mediaFieldsByType
                                    }
                                  }
                                }
                              }
                              }
                            }
                              }

                              fragment mediaFieldsByType on Media {
                               ...on ExternalVideo {
                                           id
                                           host
                                            originUrl
                                                     }
                                       ...on MediaImage {
                                                 image {
                                                    url
                                                      }
                                                        }
                                             ...on Model3d {
                                                    sources {
                                                            url
                                                            mimeType
                                                            format
                                                        filesize
                                                           }
                                                           }
                                             ...on Video {
                                                   sources {
                                                       url
                                                   mimeType
                                                     format
                                                        height
                                                       width
                                                          }
                                                         }
                                                            }
                              `
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
    fetchProducts()
</script>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product List</title>
</head>
<body>
    <TitleBar/>
    <Fetch/>
    <Content/>
    <div>
        <h2 class="sp">Shop By Accessory</h2>
        <main>
            <ul class="product-list">
              {#each products as product}
                <li class="naruto">
                  <ProductCard product={product?.node || {}} />
                </li>  
              {/each}
            </ul>
          </main>
    </div>  
</body>
