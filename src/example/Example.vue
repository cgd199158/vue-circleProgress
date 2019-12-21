<template>
  <div class="content">
    <div class="wrap_01">
      <CircleProgress :id="2" :radius="20" :progress="value" :isAnimation="true"></CircleProgress>
    </div>
    <div class="wrap_02">
      <CircleProgress id="30" :radius="20" :progress="value" barColor="red" :isAnimation="false"></CircleProgress>
    </div>
    <div class="wrap_02">
      <CircleProgress
        :widthPresent="0.8"
        :id="3"
        :gradientsColor="gradientsColor"
        :radius="20"
        :progress="value"
        :isAnimation="true"
      ></CircleProgress>
    </div>
    <button @click="handlerChange">修改值</button>
  </div>
</template>
<script>
import CircleProgress from "@/components/CircleProgress";
// import CircleProgress from 'vue-circleprogressbar';
export default {
  data() {
    return {
      value: 30,
      gradientsColor: [
        { offset: "0%", color: "#b2ed9d" },
        { offset: "100%", color: "#569b3d" }
      ]
    };
  },
  methods: {
    handlerChange() {
      this.value = 80;
    }
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


