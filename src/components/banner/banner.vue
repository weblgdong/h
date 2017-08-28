<template>
  <div class="header">
    <ul class="banner">
      <li v-for="item in bannerlist">
        <img :src="item.imgUrl"/>
      </li>
    </ul>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      bannerlist: {
        type: Array
      }
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .header
    width: 100%;
    .banner
      position relative
      width: 100%
      height: 390px
      overflow hidden
      li
        position absolute
        width: 100%
        height: 390px
        text-align: center
        img
          vertical-align: top
          max-width: 100%
          display block
</style>
