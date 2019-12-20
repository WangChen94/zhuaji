<template>
  <div>
    <z-map/>
    <div class="tab-bar">
      <div class="tab">首页</div>
      <div class="tab">首页</div>
      <div class="tab">首页</div>
      <div class="tab">首页</div>
    </div>
  </div>
</template>

<script>
import ZMap from "../../components/ZMap";
import 'weui-miniprogram/miniprogram_dist/weui-wxss/dist/style/weui.wxss';

export default {
  data () {
    return {

    }
  },

  components: {
    ZMap
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
  }
</style>
