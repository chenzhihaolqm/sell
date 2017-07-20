<template>
  <div class="cartcontrol">
    <transition name="move">
      <div class="cart-decrease icon-remove_circle_outline"
           v-show="food.count>0" @click="decreaseCart"></div>
    </transition>
    <div class="cart-count" v-show="food.count>0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click="addCart"></div>
  </div>
</template>
<script>
  import Vue from 'vue';
  export default{
    props:{
        food:{
          type:Object
        }
    },
    methods:{
      addCart(event){
        if(!this.food.count){
            Vue.set(this.food,'count',1);
        }else{
          this.food.count++;
        }
        this.$emit('add',event.target)
      },
      decreaseCart(){
        if(this.food.count){
          this.food.count--;
        }
      }
    },
    created(){

    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .cartcontrol
    font-size:0
    .cart-decrease,.cart-add
      display:inline-block
      padding:6px
      line-height:24px
      font-size:24px
      color:rgb(0,160,200)
    .cart-decrease
      display:inline-block
      &.move-enter-active,&.move-leave-active
        transition:all .4s linear
        opacity:1
        transform:translate3D(0,0,0) rotate(0deg)

      &.move-enter,&.move-leave-to
        opacity:0
        transform:translate3D(24px,0,0) rotate(180deg)
    .cart-count
      display:inline-block
      vertical-align:top
      width: 12px
      padding-top: 6px
      line-height: 24px
      font-size: 10px
      text-align:center
      color:rgb(147,153,159)
    .cart-add
      display:inline-block

</style>
