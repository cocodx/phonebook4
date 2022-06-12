<template>
  <div class="list1 wrapper">
    <div class="content">
      <div class="phoneBook" v-for="(item,key) of phoneBooks" :key="key">
        <div class="title">{{key}}</div>
        <div class="item" v-for="innerItem of item" :key="innerItem.id">
          <img src="getImageUrl(innerItem.image)" alt="">
          <div class="content1 border-bottom">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Bscroll from 'better-scroll'
  import {getServerUrl} from "@/config/sys";

  export default {
    name:"List",
    props:{
      phoneBooks:Object
    },
    methods:{
      getImageUrl(image){
        return getServerUrl('image/'+image)
      }
    },
    mounted() {
      let bs = new Bscroll('.wrapper', {})
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"

  .border-bottom
    &:before
      border-color: $borderColor

  .list1
    overflow: hidden
    position: absolute
    top: 1.58rem
    left: 0
    right: 0
    bottom: 0
    .title
      line-height: .54rem
      background: $bgColor
      padding-left: .2rem
      color: #666
      font-size: .26rem
    .item
      line-height: .76rem
      margin: .2rem
      img
        float: left
        width: .8rem
        height: .8rem
        border-radius: .2rem
      .content1
        padding-left: 1rem
        font-size: .4rem
        padding-bottom: .3rem
</style>
