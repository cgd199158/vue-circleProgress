<template>
  <div class="content">
    <div class="wrap_01">
      <CircleProgress :id="2" :radius="20" :progress="30" :isAnimation="true"></CircleProgress>
    </div>
    <div class="wrap_02">
      <CircleProgress id="30" :radius="20" :progress="30" barColor="red" :isAnimation="true"></CircleProgress>
    </div>
    <div class="wrap_02">
      <CircleProgress
        :widthPresent="0.8"
        :id="3"
        :gradientsColor="gradientsColor"
        :radius="20"
        :progress="30"
        :isAnimation="true"
      ></CircleProgress>
    </div>
  </div>
</template>
<script>
import CircleProgress from "@/components/CircleProgress";
// import CircleProgress from 'vue-circleprogressbar';
export default {
  data() {
    return {
      gradientsColor: [
        { offset: "0%", color: "#b2ed9d" },
        { offset: "100%", color: "#569b3d" }
      ]
    };
  },
  components: {
    CircleProgress
  }
};
</script>
<style lang="less" scoped>
.content {
  width: 100%;
}
.wrap_01,
.wrap_02 {
  height: 300px;
  flex: 1;
}
</style>


