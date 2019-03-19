<template>
  <div class="content" ref="box">
    <svg style="transform: rotate(-90deg)" :width="width" :height="width" xmlns="http://www.w3.org/2000/svg">
      <circle :r="(width-radius)/2"
        :cy="width/2"
        :cx="width/2"
        :stroke-width="radius"
        :stroke="backgroundColor"
        fill="none"
      />
      <circle ref="$bar"
        :r="(width-radius)/2"
        :cy="width/2"
        :cx="width/2"
        :stroke="barColor"
        :stroke-width="radius"
        :stroke-linecap="isRound ? 'round' : 'square'"
        :stroke-dasharray="(width-radius)*3.14"
        :stroke-dashoffset="isAnimation ? (width-radius) * 3.14 : (width - radius) * 3.14 * (100 - progress) / 100"
        fill="none"
      />
    </svg>
    <div class="center_text">
        <p v-if="!$slots.default" class="title">{{progress}}%</p>
        <slot></slot>
    </div>
  </div>
</template>

<script>
import _ from "lodash";
export default {
  props: {
    radius: [Number, String], // 进度条厚度
    progress: [Number, String], // 进度条百分比
    barColor: {
      type: String,
      default: "#1890ff"
    }, // 进度条颜色
    backgroundColor: {
      type: String,
      default: "rgba(0,0,0,0.3)"
    }, // 背景颜色
    isAnimation: {
      // 是否是动画效果
      type: Boolean,
      default: true
    },
    isRound: {
      // 是否是圆形画笔
      type: Boolean,
      default: true
    },
    id: {
      // 组件的id，多组件共存时使用
      type: [String, Number],
      default: 1
    },
    duration: {
      // 整个动画时长
      type: [String, Number],
      default: 1000
    },
    delay: {
      // 延迟多久执行
      type: [String, Number],
      default: 200
    },
    timeFunction: {
      // 动画缓动函数
      type: String,
      default: "cubic-bezier(0.99, 0.01, 0.22, 0.94)"
    }
  },
  data() {
    return {
      width: 100,
      idStr: `circle_progress_keyframes_${this.id}`
    };
  },
  beforeDestroy() {
    // 清除旧组件的样式标签
    document.getElementById(this.idStr) &&
      document.getElementById(this.idStr).remove();
    window.addEventListener(() => {});
  },
  mounted() {
    let self = this;
    this.setCircleWidth();
    this.setAnimation();
    // 此处不能使用window.onresize
    window.addEventListener(
      "resize",
      _.debounce(function() {
        self.setCircleWidth();
        self.setAnimation(self);
      }, 300)
    );
  },
  methods: {
    setCircleWidth() {
      let box = this.$refs.box;
      let width = box.clientWidth;
      let height = box.clientHeight;
      let cW = width > height ? height : width;
      this.width = cW;
    },
    setAnimation() {
      let self = this;
      if (self.isAnimation) {
        // 重复定义判断
        if (document.getElementById(self.idStr)) {
          console.warn("vue-circle-progress should not have same id style");
          document.getElementById(self.idStr).remove();
        }
        // 生成动画样式文件
        let style = document.createElement("style");
        style.id = self.idStr;
        style.type = "text/css";
        style.innerHTML = `
      @keyframes circle_progress_keyframes_name_${self.id} {
      from {stroke-dashoffset: ${(self.width - self.radius) * 3.14}px;}
      to {stroke-dashoffset: ${((self.width - self.radius) *
        3.14 *
        (100 - self.progress)) /
        100}px;}}
      .circle_progress_bar${
        self.id
      } {animation: circle_progress_keyframes_name_${self.id} ${
          self.duration
        }ms ${self.delay}ms ${self.timeFunction} forwards;}`;
        // 添加新样式文件
        document.getElementsByTagName("head")[0].appendChild(style);
        // 往svg元素中添加动画class
        self.$refs.$bar.classList.add(`circle_progress_bar${self.id}`);
      }
    }
  }
};
</script>
<style  scoped>
.content {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.center_text {
  position: absolute;
  color: #1890ff;
  font-size: 22px;
  font-weight: bold;
}
</style>
