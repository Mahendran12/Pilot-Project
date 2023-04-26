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

<style>
    .title {
    text-align: center;
    color: red;
    }
</style>