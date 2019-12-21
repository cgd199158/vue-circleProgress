# vue-circleprogressbar
* **一个简单的环形进度条组件**

> 最近在开发可视化大屏项目中经常会用到环形进度条,但是常用的echarts组件对环形进度条的支持不太好,写起来比较麻烦.就想着自己写一个VUE的环形组件,满足自己日常开发需求;

**2019/12/21更新内容:** 
- 完善bar的宽度逻辑,bar的宽度根据父容器的宽度进行自适应,可自定义```widthPresent```设置bar占父容器宽-- 度的比例;
- 添加渐变色```gradientsColor```
- 去掉lodash的依赖,减小组件大小
- 解决bar不随progress变化的bug

# vue-circleprogressbar
* **一个简单的环形进度条组件**
> 先上效果图
![demo.png](https://upload-images.jianshu.io/upload_images/16911973-b9a88f6edebb0307.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## Installation
```
$ npm install vue-circleprogressbar
```
## Usage
```
<template>
    <div class="wrap_01" style="height: 300px;">
        <CircleProgress  
          :id="id"
          :width="300"
          :radius="20"
          :progress="30"
          :isAnimation="true"
        ></CircleProgress>
    </div>
</template>
<script>
import CircleProgress  from 'vur-circleprogressbar';
export default {
  data() {
    return {};
  },
  components: {
    CircleProgress
  }
};
</script>

```
## Optiosn
|名字|说明|默认值|类型|
|:---|---|---|---|
|`widthPresent`|设置bar占父容器宽度的比例|`1`|`Number`|
|`gradientsColor`|bar渐变色设置|`[ { offset: "0%", color: "#b2ed9d" },{ offset: "100%", color: "#569b3d" } ]`|`Array`|
|`id`|组件的id,用于处理多组件共存|`1`|`Number, String`|
| `radius`|进度条的厚度|`20`|`Number, String`|
|`progress`|进度条百分比|`20`|`Number, String`|
|`barColor`|进度条颜色|`'#1890ff'`|`String`|
|`backgroundColor`|进度条环形背景色|`rgba(0,0,0,0.3)`|`String`|
|`isAnimation`|是否显示动画|`true`|`Bollean`|
|`isRound`|是否使用圆形画笔|`true`|`Bollean`|
|`duration`|动画时长|`1000`|`Number, String`|
|`delay`|动画延迟时间|`200`|`Number, String`|
|`timeFunction`|动画缓动函数|`'cubic-bezier(0.99, 0.01, 0.22, 0.94)'`|`String`|

## slot
|名字|说明|默认值|类型|
|:---|---|---|---|
|默认插槽|环形进度条中间的title自定义|--|--|

