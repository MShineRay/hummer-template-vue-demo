<template>
  <view>
    <text class="steps001">hello steps003</text>
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
          <!-- Customize uniformly -->
          <view v-if="$slots.icon" class="icon-wrapper">
            <slot
              name="icon"
              :index="index"
              :current-index="currentLength"
            ></slot>
          </view>
          <!-- Customize by status-->
          <view v-else class="icon-wrapper">
            <template v-if="index < currentLength">
              <slot
                v-if="$slots.reached || $slots.reached"
                name="reached"
                :index="index"
              ></slot>
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
            </template>
            <template v-else-if="index === currentLength">
              <slot
                v-if="$slots.current || $slots.current"
                name="current"
                :index="index"
              ></slot>
<!--              <md-icon v-else name="success"></md-icon>-->
              <text>icon</text>
            </template>
            <template v-else>
              <slot
                v-if="$slots.unreached || $slots.unreached"
                name="unreached"
                :index="index"
              ></slot>
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
            </template>
          </view>
          <view class="text-wrapper">
            <slot
              v-if="$slots.content"
              name="content"
              :index="index"
              :step="step"
            ></slot>
            <template v-else>
              <view class="name">
                {{ step.name }}
              </view>
              <view v-if="step.text" class="desc">
                {{ step.text }}
              </view>
            </template>
          </view>
        </view>
        <view
          class="bar"
          :class="[
          direction === 'horizontal'
            ? 'horizontal-bar'
            : 'vertical-bar',
        ]"
          :style="getStepSizeForStyle(index)"
        >
          <i
            v-if="progress[index]"
            class="bar-inner"
            :style="barInnerStyle(index)"
          ></i>
        </view>
      </template>
    </view>
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
