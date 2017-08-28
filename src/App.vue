<template>
  <div id="app">
    <v-banner :bannerlist="bannerlist"></v-banner>
  </div>
</template>

<script type="text/ecmascript-6">
  import banner from './components/banner/banner.vue';

  const ERR_NO = '000000';
  export default {
    data() {
      return {
        bannerlist: [],
        descList: []
      };
    },
    created() {
      this.$http.get('/api/getGoodsDetail.app').then((response) => {
        response = response.body.data;
        if (response['return_code'] === ERR_NO) {
          this.date = response;
          var aImgLists = this.date.goods[0].imgList;
          var bannerImg = [];
          var descImg = [];
          aImgLists.forEach((k, v) => {
            if (k.type === '101') {
              bannerImg.push(k);
            } else if (k.type === '102') {
              descImg.push(k);
            }
          });
          this.bannerlist = bannerImg.sort((a, b) => {
            return a.location - b.location;
          });
          this.descList = descImg.sort((a, b) => {
            return a.location - b.location;
          });
        }
      });
    },
    components: {
      'v-banner': banner
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">

</style>
