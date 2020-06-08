<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <div class="wrapper">
      <div class="content">
        <home-swiper :banners="banners" />
        <retcommend-view :recommends=" recommends" />
        <feature-view />
        <tab-control :titles="['流行','新款','精选']" class="tab-control" @tabclick="tabclick" />
        <goods-list :goods="showGoods" />
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "./childcomps/HomeSwiper";
import RetcommendView from "./childcomps/RetcommendView";
import FeatureView from "./childcomps/FeatureView";
import GoodsList from "components/content/goods/GoodsList";

import TabControl from "components/content/tabcontrol/TabControl";

import BSscroll from "better-scroll";

import { getHomeMultidata, getHomeGoods } from "network/home";

export default {
  name: "Home",
  components: {
    NavBar,
    HomeSwiper,
    RetcommendView,
    FeatureView,
    TabControl,
    GoodsList
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] }
      },
      currenttype: "pop"
    };
  },
  computed: {
    showGoods() {
      return this.goods[this.currenttype].list;
    }
  },
  created() {
    this.getHomeMultidata();
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
  },
  methods: {
    tabclick(index) {
      switch (index) {
        case 0:
          this.currenttype = "pop";
          break;
        case 1:
          this.currenttype = "new";
          break;
        case 2:
          this.currenttype = "sell";
      }
    },
    getHomeMultidata() {
      getHomeMultidata().then(res => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      });
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page).then(res => {
        console.log(res);
        this.goods[type].list.push(...res.data.list);
        this.goods[type].page += 1;
      });
    }
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
  z-index: 9;
}
</style>
