<template>
  <div class="card" :class="{ 'show' : showStatus, 'active' : startStatus }">
    <div class="close-button" @click="close">
      X
    </div>
    <div class="title">
      珍惜陪伴爱宠的时间，记录下你的足迹！
    </div>
    <div class="time">
      {{timeStr}}
    </div>
    <div class="info">
      <div class="distance" style="flex: 1">
        <p class="value">{{distance}}</p>
        <p class="unit">KM</p>
      </div>
      <div class="foot-number" style="flex: 1;">
        <p class="value" style="border-left: 2px solid #E8E8E9;">{{footNumber}}</p>
        <p class="unit">行走步数</p>
      </div>
    </div>
    <div class="button" @click="start">
      {{ startStatus ? '暂' : '开'}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'StartCard',
  data() {
    return{
      showStatus: false,
      startStatus: false,
      time: 0,
      timeStr: '00:00:00',
      distance: 0,
      footNumber: 0,
    }
  },
  watch: {
    time(val) {
      const hourNum = Math.floor(this.time / 3600);
      const minNum = Math.floor(this.time / 60);
      const secondNum = this.time % 60;
      let hour = hourNum > 10 ? `${hourNum}` : `0${hourNum}`;
      let min = minNum > 10 ? `${minNum}` : `0${minNum}`;
      let second = secondNum > 9 ? `${secondNum}` : `0${secondNum}`;
      let showTime = `${hourNum > 0 ? 'hourNum:' : '' }${min}:${second}`;
      this.timeStr = `${hour}:${min}:${second}`;
      this.$emit('setTime', showTime)
    }
  },
  methods: {
    close() {
      this.showStatus = false;
    },
    open() {
      this.showStatus = true;
    },
    start() {
      this.startStatus = !this.startStatus;
      this.$emit('setStatus', this.startStatus);
      if (this.startStatus) {
        this.timeInterval = setInterval(()  => {
          this.time += 1;
        }, 1000)
      } else {
        this.time = 0;
        clearInterval(this.timeInterval);
      }
    }
  }
}
</script>

<style scoped>
  .card {
    height: 375px;
    background: #FFFFFF;
    border-radius: 12px 12px 0 0;
    padding-top: 40px;
    box-sizing: border-box;
    position: absolute;
    bottom: -375px;
    width: 100%;
    text-align: center;
  }
  .show {
    bottom: 0
  }
  .title{
    font-family: PingFangSC-Medium;
    font-size: 16px;
    color: #212223;
  }
  .time{
    font-family: AvenirNext-DemiBold;
    font-size: 40px;
    color: #A1A5AC;
    height: 55px;
    line-height: 55px;
    margin-top: 25px;
    margin-bottom: 33px;
  }
  .active .time{
    color: #5780F3;
  }

  .info{
    display: flex;
  }
  .value{
    font-family: AvenirNext-Medium;
    font-size: 26px;
    color: #A1A5AC;
    letter-spacing: 1.04px;
  }

  .active .value{
    color: #5780F3;
  }

  .unit{
    font-family: PingFangSC-Medium;
    font-size: 15px;
    color: #222222;
    letter-spacing: 0.6px;
  }

  .button{
    background: #5780F3;
    box-shadow: 0 3px 8px 0 rgba(45,93,158,0.20);
    width: 65px;
    margin: 0 auto;
    margin-top: 47px;
    height: 65px;
    line-height: 65px;
    color: #FFFFFF;
    border-radius: 65px;
  }
  .active .button{
    background: #A1A5AC;
  }

  .close-button{
    position: absolute;
    top: 18px;
    right: 20px;
  }
</style>
