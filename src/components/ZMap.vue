<template>
  <map
     id="map"
     :longitude="mapCenter.longitude"
     :latitude="mapCenter.latitude"
     subkey="4ALBZ-OYRW4-XVQUN-DZAIB-5OLDT-BFFJF"
     scale="17"
     @markertap="markerClickEvent"
     @regionchange="mapViewChange"
     @end="end"
     show-location
     :style="mapStyle"/>
</template>

<script>
export default {
  props: {
    mapConfig: {
      type: Object,
      default() {
        return {
          center: [113.324520, 23.099994]
        };
      },
    },
  },
  data() {
    return{
      mapCenter: {
        longitude: '113.324520',
        latitude: '23.099994'
      },
      viewSize: {
        width: '100%',
        height: '300px'
      },
      mapStyle: 'width: 100%; height: 300px;'
    };
  },
  watch: {
    'viewSize.height'() {
      this.mapStyle = '';
      Object.keys(this.viewSize).forEach(key => {
        this.mapStyle += `${key}: ${this.viewSize[key]};`
      })
    },
    'mapConfig.location'(val) {
      console.log(val);
      this.mapCenter = {
        longitude: val[0],
        latitude: val[1]
      };
      setTimeout(() => {
        this.$map.getCenterLocation({
          success: (info) => {
            console.log(info)
          }
        })
      }, 0)
    }
  },
  mounted() {
    this.$map = wx.createMapContext('map', this);
    this.viewSize.height = `${wx.getSystemInfoSync().windowHeight  }px`;
  },
  methods: {
    markerClickEvent(info) {
      console.log(info);
    },
    mapClickEvent(info) {
      console.log(info);
    },
    end (event) {
      console.log('in end');
      console.log(event);
    }
  }
}
</script>

<style>
.card {
  padding: 10px;
}
</style>
