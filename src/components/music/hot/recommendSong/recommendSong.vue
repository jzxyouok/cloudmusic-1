<template>
  <div>
    <div class="recommend-title songlist-title">
      <p class="main-title">
        <img src="./hot-music-icon.png" alt="fff">推荐歌单</p>
      <p class="sub-title">更多></p>
    </div>
    <div class="recommend-songlist">
      <router-link class="recommend-songitem" v-for="item,index in recommendList " :to="'/subList/'+item.id">
        <lazyImg :src="item.picUrl"></lazyImg>
        <figcaption>
          {{item.name}}
          <p class="play-count"><i class="fa fa-headphones"></i>&nbsp{{Math.floor(item.playCount/10000)+'万'}}</p>
        </figcaption>
      </router-link>
    </div>
  </div>
</template>

<script>
import lazyImg from '../../../lazyImage/lazyimg';
export default {
    data() {
        return {
            recommendList: [],
        }
    },
       components:{
                lazyImg
    },
    created() {
        this.$http.get('http://localhost:3000/personalized')
            .then(function (data) {
                this.recommendList = data.body.result
            });

    },
}
</script>

<style>


</style>
