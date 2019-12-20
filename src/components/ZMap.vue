<template>
  <map
     id="map"
     longitude="113.324520"
     latitude="23.099994"
     scale="14"
     bindcontroltap="controltap"
     bindmarkertap="markertap"
     bindregionchange="regionchange"
     show-location
     :style="mapStyle"/>
</template>

<script>
export default {
  props: ['text'],
  data() {
    return{
      viewSize: {
        width: '100%',
        height: '300px'
      },
      mapStyle: 'width: 100%; height: 300px;'
    };
  },
  watch: {
    'viewSize.height'(val) {
      console.log(val);
      this.mapStyle = '';
      Object.keys(this.viewSize).forEach(key => {
        this.mapStyle += `${key}: ${this.viewSize[key]};`
      })
    }
  },
  mounted() {
    this.viewSize.height = `${wx.getSystemInfoSync().windowHeight  }px`;
  }
}
</script>

<style>
.card {
  padding: 10px;
}
</style>
