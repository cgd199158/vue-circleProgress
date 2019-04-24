# vue-circleprogressbar
* **一个简单的环形进度条组件**

![演示图片](/static/img/demo.png)
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

```
## Optiosn
|名字|说明|默认值|类型|
|:---|---|---|---|
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
