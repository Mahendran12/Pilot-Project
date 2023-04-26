<script>
    function onLogoClick(){
    console.log('click');
    window.location.href="home";
  }
  function onLogoKeyPress(event) {
    if (event.key === 'Enter' || event.key === ' ') {
      onLogoClick();
    }
  }
</script>

<div class="title">
  <h1 on:click={onLogoClick} on:keypress={onLogoKeyPress}>Womens World</h1>
</div>
<div class="flex">
  <input class=search type="text" placeholder="what are you looking for">
  <ol class="login">
      <li>Login</li>
      <li><a href="cart"><img src="https://cdn-icons-png.flaticon.com/512/3523/3523865.png" alt="Cart">cart</a></li>   
  </ol>
</div>
<style>
  .title {
    text-align: center;
    color: red;
}
.flex {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  input[type="text"]{
    width: 80%;
    padding: 12px 20px;
    margin: 15px 0;
    border: 1px solid silver;
    border-radius: 4px;
    box-sizing: border-box;
    background: url(https://img.icons8.com/ios/256/search.png)no-repeat;
    background-size: 23px, 20px;
    background-position: right 15px center;
}
  
  .login {
    display: flex;
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
  
  .login li {
    margin-right: 60px;
    cursor: pointer;
  }
  
  .login a {
    text-decoration: none;
    color: inherit;
  }
  .login li img {
    width: 15px;
    height: 15px;
    object-fit: contain;
    border-radius: 50%;
    margin-left: 5px;
  } 
  .login li:hover {
    text-decoration: underline;
  }
</style>
