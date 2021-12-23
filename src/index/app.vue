<template>
  <view class="page">
    <text class="slogan">{{slogan}}</text>
<!--    <view class="demo">-->
<!--      <steps001></steps001>-->
<!--    </view>-->
<!--    <view class="demo">-->
<!--      <steps002></steps002>-->
<!--    </view>-->
    <view class="demo">
      <text>steps003</text>
      <steps003 :steps="steps"></steps003>
    </view>
<!--    <view class="demo">-->
<!--      <text>steps004</text>-->
<!--      <steps004 :steps="steps"></steps004>-->
<!--    </view>-->
<!--    <view class="demo">-->
<!--      <text>steps005</text>-->
<!--      <steps005 :steps="steps"></steps005>-->
<!--    </view>-->
  </view>
</template>
<style lang="less" scoped>
.demo+.demo{
  margin-top: 10px;
  border-top: 1px solid red;
}
.demo{
  width: 95%;
  height: 400px;
  border: 1px solid #198cff;
  margin: 0 auto;
}
  .page{
    background: #fff;
  }
  //.slogan{
  //  font-size: 0.42rem;
  //}
</style>

<script lang="ts">
// import steps001 from '../packages/steps-base'
// import steps002 from '../packages/steps002'
import steps003 from '../packages/steps003'
// import steps004 from '../packages/steps004'
// import steps005 from '../packages/steps005'
export default {
  // pageConfig: {
  //   canScroll: false
  // },
  components: {
    // steps001,
    // steps002,
    steps003,
    // steps004,
    // steps005
  },
  data(){
    return {
      slogan: '~ Hello Tenon3 ~',
      steps:[
        {
          name: '登录/注册2',
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
