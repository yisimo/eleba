<template>
  <div id="app">
    <v-header>I am header</v-header>
    <nav class="tag border-1px">
      <div class="tag-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tag-item">
        <router-link to="/ratings">评价</router-link>
      </div>
      <div class="tag-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
  import VHeader from 'components/header/header.vue';
  export default {
    components: {
      VHeader
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import 'common/stylus/mixin.styl'

  #app
    .tag
      display: flex
      width: 100%
      height: 40px
      line-height: 40px
      border-1px(rgba(7, 17, 27, 0.1))
      .tag-item
        flex: 1
        text-align: center
        & > a
          display: block
          color: rgb(77, 85, 93)
          font-style: 14px
          &.active
            color: rgb(240, 20, 20)
</style>
