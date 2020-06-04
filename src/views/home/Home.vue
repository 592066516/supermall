<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners" />
    <retcommend-view :recommends=" recommends" />
    <feature-view />  

    <tab-control :titles="['流行','新款','精选']" class="tab-control"/>

    <ul>
      <li>列表1</li>
      <li>列表2</li>
      <li>列表3</li>
      <li>列表4</li>
      <li>列表5</li>
      <li>列表6</li>
      <li>列表7</li>
      <li>列表8</li>
      <li>列表9</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
      <li>列表10</li>
    </ul>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "./childcomps/HomeSwiper";
import RetcommendView from "./childcomps/RetcommendView";
import FeatureView from "./childcomps/FeatureView";

import TabControl from 'components/content/tabcontrol/TabControl'

import { getHomeMultidata } from "network/home";

export default {
  name: "Home",
  components: {
    NavBar,
    HomeSwiper,
    RetcommendView,
    FeatureView,
    TabControl
  },
  data() {
    return {
      banners: [],
      recommends: []
    };
  },
  created() {
    getHomeMultidata().then(res => {
      console.log(res);
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    });
  }
};
</script>

<style >
#home {
  padding-top: 44px;
}
.home-nav {

  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
.tab-control {
  position: sticky;
  top: 44px;
}
</style>
