<script setup lang="ts">
import type { Component } from 'vue'
import { computed, defineProps, withDefaults } from 'vue'
interface ButtonProps {
  size?: 'small' | 'medium' | 'large'
  type?: 'primary' | 'success' | 'danger' | 'warning' | 'info' | 'text'
  tag?: string // 自定义标签
  color?: string // 自定义颜色
  disabled?: boolean
  loading?: boolean
  round?: boolean
  circle?: boolean
  plain?: boolean
  icon?: string | Component
  loadingIcon?: string | Component
  nativeType?: 'button' | 'submit' | 'reset'
  autofocus?: boolean // 自动获取焦点
}
/**
 * 功能
 * 1. 按钮大小
 * 2. 按钮类型
 * 3. 自定义标签
 * 4. 自定义颜色
 * 5. 禁用状态
 * 6. 加载状态
 * 7. 圆角
 * 8. 圆形
 * 9. 朴素按钮
 * 10. 图标
 * 11. 原生 type 属性
 * 12. 自动获取焦点
 * 13. 加载图标
 * 14. 自定义图标
 * 15. 顺序 loading  icon slot
 *
 */

const props = withDefaults(defineProps<ButtonProps>(), {
  size: 'medium',
  type: 'primary',
  tag: 'button',
})

const classes = computed(() => [
  'fc-button',
  `fc-button--${props.size}`,
  `fc-button--${props.type}`,
  {
    'is-disabled': props.disabled,
    'is-loading': props.loading,
    'is-round': props.round,
    'is-circle': props.circle,
    'is-plain': props.plain,
  },
])
// 原生组件属性
const nativeProps = computed(() => {
  const { nativeType } = props
  return {
    type: nativeType,
    autofocus: props.autofocus,
  }
})
/**
 * css 属性
 * 1. 布局方式 display
 * 2. 文字换行 white-space
 * 3. 宽高 width height
 * 4. 字体大小 font-size
 * 5. 字体颜色 color
 * 6. 背景颜色 background-color
 * 7. 边框 border
 * 8. 圆角 border-radius
 * 9. 边框颜色 border-color
 * 10. 边框宽度 border-width
 * 11. 光标各种样式 cursor
 * 12. 字体 font-family
 * 13. 字体粗细 font-weight
 * 14. 行高 line-height
 * 15. 内边距 padding
 * 16. 外边距 margin
 * 17. 文本对齐 text-align
 * 18. 文本装饰 text-decoration
 * 19. 文本溢出 ellipsis
 * 20. 透明度 opacity
 * 21. 外边框 outline
 * 22. 溢出 overflow
 * 23. 文本垂直对齐方式 vertical-align
 * 24. 过渡动画 transition
 *
 */
</script>
<template>
  <component :is="tag" :class="classes" v-bind="nativeProps">
    <template v-if="loading">
      <slot v-if="loadingIcon" name="loading"> </slot>
      <component v-else :is="loadingIcon" />
    </template>
    <template v-if="icon">
      <component :is="icon" />
    </template>
    <span v-if="$slots.default">
      <slot />
    </span>
  </component>
</template>
