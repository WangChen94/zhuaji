<template>
  <div v-if="showStatus" class="list-page">
    <div class="list-card" v-for="info in listInfo">
      <info-card :info="info"/>
    </div>
  </div>
</template>

<script>
import InfoCard from "./InfoCard";

export default {
  components: {
    InfoCard
  },
  props: ['text'],
  data() {
    return{
      showStatus: false,
      listInfo: [{
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
      }]
    }
  },
  methods: {
    open() {
      this.showStatus = true;
    }
  }
}
</script>

<style scoped>
  .list-page{
    position: absolute;
    top: 0;
    height: 100%;
    width: 100%;
    background-color: #FFFFFF;
  }
  .list-card{
    height: 219px;
    position: relative;
  }
</style>
