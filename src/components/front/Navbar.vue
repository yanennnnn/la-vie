<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <a class="navbar-brand" href="#">la vie</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse"
      data-target="#navbarNavAltMarkup"
      aria-controls="navbarNavAltMarkup" aria-expanded="false"
      aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
      <div class="navbar-nav">
        <router-link to="/index" href="#"
          class="nav-item nav-link">首頁</router-link>
        <router-link to="/Products" href="#"
          class="nav-item nav-link">商品</router-link>
        <router-link to="/Cart" href="#"
          class="nav-item nav-link">購物車</router-link>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {};
  },
};
</script>

<style>

</style>
