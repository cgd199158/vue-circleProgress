<template>
  <div class="content">
    <div class="wrap_01">
      <CircleProgress  
          :id="2"
          :width="300"
          :radius="20"
          :progress="30"
          :isAnimation="true"
          ></CircleProgress>
    </div>
    <div class="wrap_02">
      <CircleProgress  
          id="30"
          :width="300"
          :radius="20"
          :progress="30"
          barColor="red"
          :isAnimation="true"
          ></CircleProgress>
    </div>
  </div>
</template>
<script>
// import CircleProgress from "../components/CircleProgress";
import CircleProgress from 'vue-circleprogressbar';
export default {
  data() {
    return {};
  },
  components: {
    CircleProgress
  }
};
</script>
<style lang="less" scoped>
.content{
  width: 100%;
}
.wrap_01, .wrap_02{
    height: 300px;
    flex: 1;
}
</style>


