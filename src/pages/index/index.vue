<template>
  <view class="content">
    <scroll-view
      :scroll-y="true"
      class="main box-border absolute"
      style="height: 100vh"
      :throttle="false"
      @scroll="wxsIndex.scrollEvent"
    >
      <image class="logo" src="/static/logo.png" />
      <view class="text-area">
        <text class="title">{{ title }}</text>
      </view>
    </scroll-view>
  </view>
</template>

<script module="wxsIndex" lang="wxs">
var opacityValue = 0
function scrollEvent(e, ins) {
  console.log('scrollEvent happen')
  ins.callMethod('targetMethod', 666)
}
module.exports = {
  scrollEvent: scrollEvent,
}

</script>

<!-- <script setup lang="ts">
import { ref } from 'vue'
const title = ref('Hello')
const targetMethod = (value: number) => {
  console.log(value)
}

defineExpose({
  targetMethod
})
</script> -->

<script lang="ts">
import { defineComponent } from "vue"
export default defineComponent({
  // wxsCallMethods: [
  //   'targetMethod'
  // ],
  methods: {
    targetMethod(value: number) {
      console.log('[targetMethod in methods] triggered', value)
    }
  },
  setup() {
    const targetMethod = (value: number) => {
      console.log('[targetMethod in setup] triggered', value)
    }

    return { targetMethod }
  }
})
</script>

<style>
.conten .content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  overflow: auto;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
  height: 200vh;
}
</style>