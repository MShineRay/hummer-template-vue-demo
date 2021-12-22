<template>
  <view class="page">
    <text class="slogan">{{slogan}}</text>
    <view class="demo">
      <steps001></steps001>
    </view>
    <view class="demo">
      <steps002></steps002>
    </view>
    <view class="demo">
      <steps003 :steps="steps"></steps003>
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
import steps001 from '../packages/steps-base'
import steps002 from '../packages/steps002'
import steps003 from '../packages/steps003'
export default {
  pageConfig: {
    canScroll: false
  },
  components: {
    steps001,
    steps002,
    steps003
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
