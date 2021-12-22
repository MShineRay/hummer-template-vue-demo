<template>
  <view class="page">
    <text class="slogan">{{slogan}}</text>
    <view class="demo">
      <step001></step001>
    </view>
    <view class="demo">
      <step001></step001>
    </view>
  </view>
</template>
<style lang="less" scoped>
.demo+.demo{
  margin-top: 10px;
  border-top: 1px solid red;
}
  //.page{
  //  width: 100%;
  //  height: 100%;
  //  display: flex;
  //  justify-content: center;
  //  align-items: center;
  //}
  //.slogan{
  //  font-size: 0.42rem;
  //}
</style>

<script lang="ts">
import MdSteps from '../packages/steps-base'
export default {
  pageConfig: {
    canScroll: false
  },
  components: {
    step001:MdSteps
  },
  data(){
    return {
      slogan: '~ Hello Tenon3 ~',
      steps:[
        {
          name: '登录/注册',
        },
        {
          name: '申请征信报告',
        },
        {
          name: '提取征信报告',
        },
      ]
    }
  },
  methods: {
  }
}
</script>
