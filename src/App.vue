<template>
  <div id="app">
    <v-header>I am header</v-header>
    <nav class="tag">
      <div class="tag-item">商品</div>
      <div class="tag-item">评价</div>
      <div class="tag-item">商家</div>
    </nav>
    <main>I am content</main>
  </div>
</template>

<script>
  import VHeader from './components/header/header.vue';
  export default {
    components: {
      VHeader
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  #app
    .tag
      display: flex
      width: 100%
      height: 40px
      line-height: 40px
      .tag-item
        flex: 1
        text-align: center
</style>
