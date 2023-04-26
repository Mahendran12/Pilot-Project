<script>
    function onLogoClick(){
    console.log('click');
    window.location.href="products";
  }
  function onLogoKeyPress(event) {
    if (event.key === 'Enter' || event.key === ' ') {
      onLogoClick();
    }
  }
</script>

<header>
    <ol>
        <li>New Launch</li>
        <li>Shop By Ayurveda</li>
        <li on:click={onLogoClick} on:keypress={onLogoKeyPress}>Shop By Accessory</li>
        <li>Review And Feedback</li>
    </ol>
</header>
<style>
    header ol li{
    display: inline;
    list-style: none;
    padding-right: 70px;
    color: #e40d0d;
    font-size: 20px;
    cursor: pointer;   
}
header {
    background-color: #333;
    color: #fff;
    padding: 20px;
    text-align: center;
  }
</style>