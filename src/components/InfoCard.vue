<template>
  <div class="info-card">
    <div class="card-head">
      <div class="head-pic">

      </div>
      <div class="base-info">
        <p class="name">
          {{info.name}}
        </p>
        <p class="info">
          宠物：{{info.petType}}{{info.petSex}}
        </p>
      </div>
      <div class="server-info">
        <p>已结伴：{{info.serverNumber}}次</p>
      </div>
    </div>
    <div class="loc-info">
      <div class="location">
        {{info.location}}
      </div>
      <div class="extra-info">
        <span>距您{{info.distance}}米</span>
        <span v-if="info.publishInfo.status">今天{{info.publishInfo.time}}出发</span>
      </div>
    </div>
    <div class="card-footer">
      <span>{{info.publishInfo.status ? '正在结伴中...': ''}}</span>
      <div style="float: right">
        <div class="base-button">邀请结伴</div>
        <div class="base-button" style="margin-left: 15px;">私聊</div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
      default() {
        return{
          name:'粉扑大王',
          petType: '美短',
          petSex: '公',
          serverNumber: 1,
          location: '北京市朝阳区望京澳洲康都小区',
          distance: 100,
          publishInfo: {
            status: true,
            time: '12:30'
          }
        }
      }
    }
  },
  data() {
    return{

    }
  }
}
</script>

<style scoped>
  .info-card{
    padding: 0 15px;
    width: 95%;
    position: absolute;
    left: 50%;
    bottom: 15px;
    transform: translate(-50%, 0);
    height: 204px;
    background: #FFFFFF;
    box-shadow: 0 2px 8px 0 rgba(45,93,158,0.20);
    border-radius: 10px;
    box-sizing: border-box;
    margin-top: 15px;
  }

  .card-head {
    overflow: hidden;
    height: 68px;
    padding: 15px 0 15px 0;
    border-bottom: 1px solid #E8E8E9;
    box-sizing: border-box;
  }
  .head-pic{
    height: 38px;
    width: 38px;
    border-radius: 38px;
    background-color: #5780F3;
    float: left;
    margin-right: 14px;
  }
  .base-info{
    height: 38px;
    float: left;
  }
  .name{
    font-family: PingFangSC-Semibold;
    font-size: 16px;
    color: #222222;
    letter-spacing: -0.11px;
  }
  .info{
    font-family: PingFangSC-Regular;
    font-size: 12px;
    color: #556077;
    letter-spacing: -0.08px;
  }
  .server-info{
    height: 38px;
    font-family: PingFangSC-Regular;
    font-size: 12px;
    color: #556077;
    letter-spacing: -0.08px;
    float: right;
    position: relative;
    width: 65px;

  }
  .server-info p {
    position: absolute;
    bottom: 0;
  }

  .loc-info{
    border-bottom: 1px solid #E8E8E9;
    padding: 15px 0;
    box-sizing: border-box;
  }

  .location{
    font-family: PingFangSC-Regular;
    font-size: 14px;
    color: #222222;
    letter-spacing: -0.09px;
    margin-bottom: 9px;
  }

  .extra-info{
    font-family: PingFangSC-Regular;
    font-size: 14px;
    color: #556077;
    letter-spacing: -0.09px;
  }
  .card-footer{
    margin-top: 15px;
  }
  .card-footer span{
    font-family: PingFangSC-Regular;
    font-size: 12px;
    color: #222222;
    letter-spacing: -0.08px;
    line-height: 30px;
  }
</style>
