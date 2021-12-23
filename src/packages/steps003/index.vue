<template>
  <view
    ref="stepsRef"
    class="md-steps"
    :class="{
      'md-steps-vertical': direction == 'vertical',
      'md-steps-horizontal': direction == 'horizontal',
      'vertical-adaptive':
        direction == 'vertical' && verticalAdaptive,
      'no-current': currentLength % 1 !== 0,
    }"
  >
    <template
      v-for="(step, index) of steps"
      :key="`steps-${index}`"
    >
      <view
        class="step-wrapper"
        :class="[getStepStatusClass(index)]"
      >
        <view v-if="$slots.icon" class="icon-wrapper">
          <view
            name="icon"
            :index="index"
            :current-index="currentLength"
          ></view>
        </view>
        <view v-else class="icon-wrapper">
          <view v-if="index < currentLength">
            <view
              v-if="$slots.reached || $slots.reached"
              name="reached"
              :index="index"
            ></view>
            <view v-else class="step-node-default">
              <view
                class="step-node-default-icon"
                style="
                  width: 6px;
                  height: 6px;
                  border-radius: 50%;
                "
              ></view>
            </view>
          </view>
          <view v-else-if="index === currentLength">
            <view
              v-if="$slots.current || $slots.current"
              name="current"
              :index="index"
            ></view>
            <text v-else>icon</text>
          </view>
          <view v-else>
            <view
              v-if="$slots.unreached || $slots.unreached"
              name="unreached"
              :index="index"
            ></view>
            <view v-else class="step-node-default">
              <view
                class="step-node-default-icon"
                style="
                  width: 6px;
                  height: 6px;
                  border-radius: 50%;
                "
              ></view>
            </view>
          </view>
        </view>
        <view class="text-wrapper">
          <view
            v-if="$slots.content"
            name="content"
            :index="index"
            :step="step"
          ></view>
          <view v-else>
            <text class="name">
              {{ step.name }}1
            </text>
            <text v-if="step.text" class="desc">
              {{ step.text }}
            </text>
          </view>
        </view>
      </view>
      <div
        class=""
        :class="[
          direction === 'horizontal'
            ? 'bar__horizontal-bar'
            : 'vertical-bar',
        ]"
        :style="getStepSizeForStyle(index)"
        v-if="index!==steps.length-1"
      >
        <i
          v-if="progress[index]"
          class="bar-inner"
          :style="barInnerStyle(index)"
        ></i>
      </div>
    </template>
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
.md-steps{
  display: flex;
  justify-content: space-around;
  font-size: 28px;
  //background-color: red;
  &.md-steps-horizontal{
    align-items: center;
    padding: 40px 100px 100px;
    .step-wrapper{
      margin: 0 4px;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      &.reached{
        .text-wrapper{
          .name{
            color: #41485D;//var(--md-steps-text-color)
          }
        }
      }
      &.current{
        .text-wrapper{
          .name{
            color: #198cff;//var(--md-steps-color-active)
          }
        }
      }
    }
    .text-wrapper{
      top: 100%;
      padding-top: 20px;// var(--md-steps-text-gap-horizontal)
      text-align: center;
      .name{
        color: #858B9C;//var(--md-steps-desc-color)
      }
      .desc{
        margin-top: 10px;
        color: #858B9C;// var(--md-steps-desc-color)
      }
    }
    &.no-current{
      .reached:last-of-type{
        display: none!important;
      }
    }
  }
  //&.md-steps-vertical{
  //  align-items: flex-start;
  //  padding: 40px;
  //  flex-direction: column;
  //  &.vertical-adaptive{
  //    justify-content: normal;
  //    padding: 40px 40px 8px;
  //    .bar.vertical-bar{
  //      flex:1;
  //    }
  //  }
  //  .step-wrapper{
  //    width: 100%;
  //    margin: 4px 0;
  //    align-items: stretch;
  //    .icon-wrapper{
  //      position: relative;
  //      .step-node-default{
  //        min-width: 32px;// var(--md-steps-icon-size)
  //        min-height: 32px;//var(--md-steps-icon-size)
  //      }
  //    }
  //    .text-wrapper{
  //      left: 32px;// var(--md-steps-icon-size)
  //      padding-left: 40px;// var(--md-steps-text-gap-vertical)
  //      .name,
  //      .desc{
  //        white-space: normal;
  //      }
  //      .name{
  //        color: #41485D;//var(--md-steps-text-color)
  //      }
  //      .desc{
  //        margin-top: 18px;
  //        color: #858B9C;//var(--md-steps-desc-color)
  //      }
  //    }
  //  }
  //}
  .icon-wrapper{
    display: flex;
    justify-content: center;
    align-items: center;
    color: #E2E4EA;// var(--md-steps-color)
    >div{
      display: flex;
      justify-content: center;
      align-items: center;
    }
    &:nth-child(2){
      display: none;
    }
    .step-node-default-icon{
      background: #E2E4EA;//var(--md-steps-color)
    }
  }
  .step-wrapper{
    display: flex;
    position: relative;
    min-width:32px;// var(--md-steps-icon-size)
    min-height:32px;// var(--md-steps-icon-size)
    .icon-wrapper{
      min-width:32px;// var(--md-steps-icon-size)
      min-height:32px;// var(--md-steps-icon-size)
      .md-icon{
        width:32px;// var(--md-steps-icon-size)
        height:32px;// var(--md-steps-icon-size)
        font-size:32px;// var(--md-steps-icon-size)
      }
    }
    .text-wrapper{
      position: absolute;
      .name,
      .desc{
        white-space: nowrap;
      }
      .name{
        line-height:28px; //var(--md-steps-text-font-size)
        font-size:28px; //var(--md-steps-text-font-size)
      }
      .desc{
        line-height:26px;// var(--md-steps-text-font-size)
        font-size:26px;// var(--md-steps-desc-font-size)
      }
    }
    &.reached,
    &.current{
      .icon-wrapper{
        color: #198cff;//var(--md-steps-color-active);
        .step-node-default-icon{
          background: #198cff;//var(--md-steps-color-active)
        }
      }
    }
  }
  .bar{
    position: relative;
    background-color: #E2E4EA;
    overflow: hidden;
    flex: 1 1 auto;
    height: 2px;
    .bar-inner{
      z-index: 10;
      position: absolute;
      top: 0;
      left: 0;
      display: block;
      content: '';
      transition: all linear 1s;
    }
    &.horizontal-bar{
      flex: 1;
      height: 2px;//var(--md-steps-border-size)
      .bar-inner{
        width: 100%;
        height: 1px;//var(--md-steps-border-size)
        background-color: #198cff;//var(--md-steps-color-active);
      }
    }
    //&.vertical-bar{
    //  left: 16px;
    //  width: 1px;//var(--md-steps-border-size)
    //  transform: translateX(-50%);
    //  .bar-inner{
    //    width: 1px;//var(--md-steps-border-size)
    //    height: 100%;
    //    background-color: #198cff;//var(--md-steps-color-active);
    //  }
    //}
    &:last-of-type{
      &.horizontal-bar{
        display: none;
      }
      &.vertical-bar{
        visibility: hidden;
      }
    }
  }
  .bar__horizontal-bar{
    position: relative;
    background-color: #E2E4EA;
    overflow: hidden;
    flex: 1 1 auto;
    height: 2px;
    .bar-inner{
      z-index: 10;
      position: absolute;
      top: 0;
      left: 0;
      display: block;
      content: '';
      transition: all linear 1s;
      width: 100%;
      height: 1px;//var(--md-steps-border-size)
      background-color: #198cff;//var(--md-steps-color-active);
    }
    &:last-of-type{
      &.horizontal-bar{
        display: none;
      }
      &.vertical-bar{
        visibility: hidden;
      }
    }
  }
  .bar__horizontal-bar:last-of-type{
    display: none;
  }
}
</style>
