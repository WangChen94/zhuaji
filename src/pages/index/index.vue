<template>
  <div style="position: relative;overflow: hidden">
    <div class="content">
      <z-map :mapConfig="mapConfig"/>
      <div class="button foot" :class="{ 'active' : startStatus }" @click="start">
        {{startStatus ? showTime : '足迹'}}
      </div>
      <div class="button list" @click="openListPage">
        列
      </div>
      <div class="button publish" :class="{ 'active' : startStatus }">
        {{publishStatus ? '正在结伴中…' : '发布结伴' }}
      </div>
    </div>
    <list-page ref="listPage"/>
    <div class="tab-bar">
      <div class="tab">结伴</div>
      <div class="tab">上门</div>
      <div class="tab">社区</div>
      <div class="tab">消息</div>
      <div class="tab">我的</div>
    </div>
    <start-card ref="startCard" @setTime="setTime" @setStatus="setStartStatus"/>
  </div>
</template>

<script>
import ZMap from "../../components/ZMap";
import StartCard from "../../components/StartCard";
import InfoCard from "../../components/InfoCard";
import ListPage from "../../components/ListPage";
import 'weui-miniprogram/miniprogram_dist/weui-wxss/dist/style/weui.wxss';

export default {
  data () {
    return {
      mapConfig: {
        location: []
      },
      publishStatus: false,
      startStatus: false,
      showTime: '00:00'
    }
  },

  components: {
    ZMap,
    StartCard,
    ListPage,
    InfoCard
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
    start() {
      this.$refs.startCard.open();
    },
    openListPage() {
      this.$refs.listPage.open();
    },
    setTime(val) {
      this.showTime = val;
    },
    setStartStatus(val) {
      this.startStatus = val;
    }
  }
}
</script>

<style scoped>
  .content{
    position: relative;
  }

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

  .button{
    box-shadow: 0 2px 8px 0 rgba(45,93,158,0.20);
    border-radius: 20px;
    border-radius: 20px;
    font-family: PingFangSC-Medium;
    font-size: 16px;
    letter-spacing: -0.11px;
    height: 40px;
    line-height: 40px;
    box-sizing: border-box;
    text-align: center;
    cursor: pointer;
  }

  .list{
    top: 20px;
    right: 19px;
    position: absolute;
    width: 38px;
    height: 38px;
    line-height: 38px;
    border-radius: 38px;
    background: #FFFFFF;
    color: #222222;
  }

  .foot{
    background: #FFFFFF;
    color: #222222;
    position: absolute;
    top: 20px;
    left: 20px;
    padding: 0 15px;
  }

  .foot.active{
    color: #5780F3;
  }

  .publish{
    background: #5780F3;
    color: #FFFFFF;
    position: absolute;
    bottom: 80px;
    left: 20px;
    padding: 0 15px;
  }
</style>
<style>
  .base-button {
    border: 1px solid rgba(45,93,158,0.20);
    border-radius: 15px;
    height: 30px;
    width: 78px;
    line-height: 30px;
    text-align: center;
    cursor: pointer;
    display: inline-block;
    font-family: PingFangSC-Regular;
    font-size: 14px;
    color: #556077;
    letter-spacing: -0.09px;
  }
</style>
