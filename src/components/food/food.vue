<template>
  <transition name="move">
    <div v-show="showFlag" class="food">
      <div class="image-header">
        <img :src="food.image"></img>
        <div class="back" @click="hide">
          <i class="icon-arrow_lift"></i>
        </div>
      </div>
      <div class="content">
        <div class="detail">
          <span class="sell-count">月售{{food.sellCount}}</span>
          <span class="rating">好评率{{food.rating}}%</span>
        </div>
        <div class="price">
          <span class="now">¥{{food.price}}</span><span class="old" v-if="food.oldPrice">{{food.oldPrice}}</span>
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
  export default{
    props:{
      food:{
        type:Object
      }
    },
    data(){
      return {
          showFlag:false
      }
    },
    methods:{
      show(){
          this.showFlag =true;
      },
      hide(){
        this.showFlag =false;
      }
    }

  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .food
    position:fixed
    left:0
    top:0
    bottom: 48px
    width:100%
    z-index:30
    background:#fff
    transform:translate3d(0,0,0)
    &.move-enter-active,&.move-leave-active
      transition:all .3s linear
    &.move-enter,&.move-leave-to
      transform:translate3d(100%,0,0)
    .image-header
      position:relative
      width:100%
      height:0
      padding-top:100%
      img
        position:absolute
        left:0
        top:0
        width:100%
        height:100%
      .back
        position:absolute
        top: 10px
        left:0
        .icon-arrow_lift
          display:inline-block
          padding: 10px
          font-size:20px
          color:#fff

    .content
      padding: 18px
      .title
        line-height: 14px
        margin-bottom: 8px
        font-size: 14px
        font-weight:700
        color:rgb(7,17,27)
      .detail
        margin-bottom: 18px
        line-height: 10px
        font-size:0
        .sell-count,.rating
          font-size: 10px

</style>
