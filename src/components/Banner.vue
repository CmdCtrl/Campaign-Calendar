<template>
<div class="banner">
    <img src="../assets/banner.png" alt="">
      <div class="campaign-logo">
        <h1>Campaign</h1>
      </div>
      <div class="chronicle-logo">
        <h1>Chronicle</h1>
      </div>
</div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>

* {
    margin: 0;
    padding: 0;
}

.campaign-logo {
  position: fixed;
  top: 4px;
  left: 16px;
  font-size: 7vh;
  color: #FFF;
}

.chronicle-logo {
  position: fixed;
  top: 94px;
  left: 16px;
  font-size: 7vh;
  color: #FFF;
}

img {
    width: 100%;
    height: 186px;
    top: 0;
    display: flex;
}

@media screen and (max-width: 640px) {
  .campaign-logo, .chronicle-logo {
      font-size: 8vw;
      -webkit-text-stroke-width: 1px; 
      -webkit-text-stroke-color: gray; 
  }
}
</style>