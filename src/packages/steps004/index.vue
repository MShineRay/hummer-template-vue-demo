<template>
  <view class="md-steps md-steps-horizontal no-current">
    <view class="step-wrapper reached">
      <view class="icon-wrapper">
        <view class="step-node-default">
          <!--节点-->
          <view class="step-node-default-icon" style="width: 0.28rem; height: 0.28rem; border-radius: 50%;"></view>
        </view>
      </view>
      <view class="text-wrapper">
        <text class="name">登录</text>
      </view>
    </view>
    <view
      class="bar horizontal-bar"
      style="flex: 1;height: 1px;"
    >
      <i class="bar-inner" style="transform: translate3d(0%, 0px, 0px); transition: all 0s linear 0s;"></i>
    </view>
    <view class="step-wrapper reached current">
      <view class="icon-wrapper">
        <view class="step-node-default">
          <view class="step-node-default-icon" style="width: 6px; height: 6px; border-radius: 50%;"></view>
        </view>
      </view>
      <view class="text-wrapper">
        <text class="name">开通</text></view>
    </view>
    <view class="bar horizontal-bar"></view>
  </view>
</template>

<script lang="ts">
import {defineComponent} from 'vue'
import {stepsProps, useSteps} from './use-steps'

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

<style lang="less" scoped>
.steps001 {
  background-color: red;
}

.md-steps {
  display: flex;
  justify-content: space-around;
  font-size: 28px;

  &.md-steps-horizontal {
    align-items: center;
    padding: 40px 100px 100px;

    .step-wrapper {
      margin: 0 4px;
      justify-content: center;
      align-items: center;
      flex-direction: column;

      &.reached {
        .text-wrapper {
          .name {
            color: #41485D; //var(--md-steps-text-color)
          }
        }
      }

      &.current {
        .text-wrapper {
          .name {
            color: #198cff; //var(--md-steps-color-active)
          }
        }
      }
    }

    .text-wrapper {
      top: 100%;
      padding-top: 20px; // var(--md-steps-text-gap-horizontal)
      text-align: center;

      .name {
        color: #858B9C; //var(--md-steps-desc-color)
      }

      .desc {
        margin-top: 10px;
        color: #858B9C; // var(--md-steps-desc-color)
      }
    }

    &.no-current {
      .reached:last-of-type {
        display: none !important;
      }
    }
  }

  &.md-steps-vertical {
    align-items: flex-start;
    padding: 40px;
    flex-direction: column;

    &.vertical-adaptive {
      justify-content: normal;
      padding: 40px 40px 8px;

      .bar.vertical-bar {
        flex: 1;
      }
    }

    .step-wrapper {
      width: 100%;
      margin: 4px 0;
      align-items: stretch;

      .icon-wrapper {
        position: relative;

        .step-node-default {
          min-width: 32px; // var(--md-steps-icon-size)
          min-height: 32px; //var(--md-steps-icon-size)
        }
      }

      .text-wrapper {
        left: 32px; // var(--md-steps-icon-size)
        padding-left: 40px; // var(--md-steps-text-gap-vertical)
        .name,
        .desc {
          white-space: normal;
          font-size: 30px;

        }

        .name {
          color: #41485D; //var(--md-steps-text-color)
          font-size: 30px;
        }

        .desc {
          margin-top: 18px;
          color: #858B9C; //var(--md-steps-desc-color)
        }
      }
    }
  }

  .icon-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    color: #E2E4EA; // var(--md-steps-color)
    > div {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    &:nth-child(2) {
      display: none;
    }

    .step-node-default-icon {
      background: #E2E4EA; //var(--md-steps-color)
    }
  }

  .step-wrapper {
    display: flex;
    position: relative;
    min-width: 32px; // var(--md-steps-icon-size)
    min-height: 32px; // var(--md-steps-icon-size)
    .icon-wrapper {
      min-width: 32px; // var(--md-steps-icon-size)
      min-height: 32px; // var(--md-steps-icon-size)
      .md-icon {
        width: 32px; // var(--md-steps-icon-size)
        height: 32px; // var(--md-steps-icon-size)
        font-size: 32px; // var(--md-steps-icon-size)
      }
    }

    .text-wrapper {
      position: absolute;

      .name,
      .desc {
        white-space: nowrap;
      }

      .name {
        line-height: 28px; //var(--md-steps-text-font-size)
        font-size: 28px; //var(--md-steps-text-font-size)
      }

      .desc {
        line-height: 26px; // var(--md-steps-text-font-size)
        font-size: 26px; // var(--md-steps-desc-font-size)
      }
    }

    &.reached,
    &.current {
      .icon-wrapper {
        color: #198cff; //var(--md-steps-color-active);
        .step-node-default-icon {
          background: #198cff; //var(--md-steps-color-active)
        }
      }
    }
  }

  .bar {
    position: relative;
    //background-color: #E2E4EA; //var(--md-steps-color)
    background-color: unset;
    overflow: hidden;
    .bar-inner {
      z-index: 10;
      position: absolute;
      top: 0;
      left: 0;
      display: block;
      content: '';
      transition: all linear 1s;
    }

    &.horizontal-bar {
      flex: 1;
      height: 1px; //var(--md-steps-border-size)
      .bar-inner {
        width: 100%;
        height: 1px; //var(--md-steps-border-size)
        background-color: #198cff; //var(--md-steps-color-active);
      }
    }

    &.vertical-bar {
      left: 16px;
      width: 1px; //var(--md-steps-border-size)
      transform: translateX(-50%);

      .bar-inner {
        width: 1px; //var(--md-steps-border-size)
        height: 100%;
        background-color: #198cff; //var(--md-steps-color-active);
      }
    }

    &:last-of-type {
      &.horizontal-bar {
        display: none;
      }

      &.vertical-bar {
        visibility: hidden;
      }
    }
  }
}
</style>
