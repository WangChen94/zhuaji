<template>
  <div>
    <z-map :mapConfig="mapConfig"/>
    <div class="tab-bar">
      <div class="tab">结伴</div>
      <div class="tab">上门</div>
      <div class="tab">社区</div>
      <div class="tab">消息</div>
      <div class="tab">我的</div>
    </div>
  </div>
</template>

<script>
import ZMap from "../../components/ZMap";
import 'weui-miniprogram/miniprogram_dist/weui-wxss/dist/style/weui.wxss';

export default {
  data () {
    return {
      mapConfig: {
        location: []
      }
    }
  },

  components: {
    ZMap
  },
  mounted() {
    wx.getLocation({
      isHighAccuracy: true,
      highAccuracyExpireTime: 3000,
      success:  (info) => {
        const { longitude, latitude } = info;
        this.mapConfig.location = [longitude, latitude];
        console.log(location);
      }
    });
  },
  methods: {

  }
}
</script>

<style scoped>
  .tab-bar{
     height: 30px;
     display: flex;
     position: fixed;
     bottom: 0;
     width: 100%;
   }
  .tab{
    flex: 1;
    text-align: center;
    background: #ffffff;
    font-family: PingFangSC-Medium;
    font-size: 11px;
    color: #222222;
    letter-spacing: -0.07px;
  }
</style>
