<template>
  <view>
    <text class="steps001">hello steps002</text>
  </view>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { stepsProps, useSteps } from './use-steps'
export default defineComponent({
  name: 'MdSteps',
  props: stepsProps,
  setup(props) {
    return {
      ...useSteps(props),
    }
  }
})
</script>

<style lang="less">
.steps001{
  //background-color: red;
}
</style>
