<template>
<div id="home">
<nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
  <home-swiper :banners="banners"></home-swiper>
  <recommend-view :recommends="recommends"></recommend-view>
</div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwiper from './childComps/HomeSwiper'
import RecommendView from './childComps/RecommendView'

import {getHomeMultidata} from "network/home"
// import Swiper from 'components/common/swiper/Swiper'
// import SwiperItem from 'components/common/swiper/SwiperItem'



export default {
name : "Home",
components:{
  NavBar,
  HomeSwiper,
  RecommendView
},
data(){
  return{
    banners:[],
    recommends:[]
  }
},
created(){
  //1.请求多个数据
  getHomeMultidata().then(res=>{
    this.banners = res.data.data.banner.list;
    this.recommends = res.data.data.recommend.list;
  })
}
}
</script>
<style scope>
.home-nav{
  background-color: var(--color-tint);
  color: #fff;
}
</style>