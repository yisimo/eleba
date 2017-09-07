<template>
  <div class="cartcontrol">
    <transition name="move">
      <div class="cart-decrease" v-show="food.count>0" @click.stop.prevent="decreaseCart">
        <i class="inner icon-remove_circle_outline"></i>
      </div>
    </transition>
    <div class="cart-count" v-show="food.count>0">{{ food.count }}</div>
    <div class="cart-add icon-add_circle" @click.stop.prevent="addCart"></div>
  </div>
</template>

<script type="text/ecmascript-6">
  import Vue from 'vue';

  export default {
    props: {
      food: {
        type: Object
      }
    },
    methods: {
      addCart(event) {
        if (!this.food.count) {
          Vue.set(this.food, 'count', 1);
        } else {
          this.food.count ++;
        }
        this.$emit('add', event.target);
      },
      decreaseCart(event) {
        if (this.food.count) {
          this.food.count--;
        }
      }
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
.cartcontrol
  font-size: 0
  .cart-decrease
    display: inline-block
    padding: 6px
    opacity: 1
    transition: all 0.4s linear
    .inner
      display: inline-block
      line-height: 24px
      font-size: 24px
      color: rgb(0, 160, 220)
      transition: all 0.4s linear
      transform: rotate(0)
    &.move-enter, &.move-leave-to
      opacity: 0
      transform: translate3d(24px, 0, 0)
      .inner
        transform: rotate(180deg)
  .cart-count
    display: inline-block
    vertical-align: top
    text-align: center
    padding-top: 6px
    line-height:24px
    width: 12px
    font-size: 10px
    color: rgb(147, 153, 159)
  .cart-add
    display: inline-block
    padding: 6px
    line-height: 24px
    font-size: 24px
    color: rgb(0, 160, 220)
</style>
