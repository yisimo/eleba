<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
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
    <keep-alive>
      <router-view :seller="seller"></router-view>
    </keep-alive>
  </div>
</template>

<script>
  import {urlParse} from 'common/js/util';
  import VHeader from 'components/header/header.vue';

  const ERR_OK = 0;

  export default {
    data() {
      return {
        seller: {
          id: (() => {
            let queryParam = urlParse();
            return queryParam.id;
          })()
        }
      };
    },
    created() {
      this.$http.get('/api/seller?id' + this.seller.id).then((response) => {
        response = response.body;
        if (response.errno === ERR_OK) {
          this.seller = Object.assign({}, this.seller, response.data);
        }
      });
    },
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
