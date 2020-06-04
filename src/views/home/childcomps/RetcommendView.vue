<template>
  <div class="recommend">
    <div v-for="item in recommends" :key="item.link" class="item-recommend">
      <a :href="item.link">
        <img :src="item.image" alt />
        <div>{{item.title}}</div>
      </a>
    </div>
  </div>
</template>
<script>
export default {
  name: "RetcommendView",
  props: {
    recommends: {
      type: Array,
      default() {
        return [];
      }
    }
  }
};
</script>
<style >
.recommend {
  display: flex;
  width: 100%;
  text-align: center;
  font-size:12px;
  padding: 15px 0 30px;
  border-bottom: 8px solid #eee;
}
.item-recommend {
  flex: 1;
}
.recommend img{
    width: 70px;
    height: 65px;
    margin-bottom: 10px;
    
}
</style>