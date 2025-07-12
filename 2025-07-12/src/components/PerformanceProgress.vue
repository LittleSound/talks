<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  /** 提示名称 */
  name: string
  /** 次要描述，可选 */
  secondary?: string
  /** UnoCSS 图标类 */
  icon: string
  /** 实际进度值 */
  progress: number
  /** 是否高亮显示 */
  highlight?: boolean
  /**
   * 可选的显示区间，默认 `[0, 100]`。
   * 当传入 `[min, max]` 时，会将 `progress` 按该区间映射到 0-100% 进行渲染，
   * 适合展示数值差距较小的对比。
   */
  interval?: [number, number]

  colorClass?: string

}>()

/**
 * 将实际 progress 映射到 0-100 的显示百分比。
 */
const widthPercent = computed(() => {
  const [min, max] = props.interval ?? [0, 100]
  // 避免除 0
  if (max === min)
    return 0
  const percent = ((props.progress - min) / (max - min)) * 100
  // 保证范围在 0-100 之间
  return Math.max(0, Math.min(100, percent))
})
</script>

<template>
  <div flex items-center gap4 rounded-md p3 :class="[highlight && 'bg-sky/20']">
    <div w-30 flex items-center gap1>
      <div :class="icon" w-4 op80 />
      <span text-sm>{{ name }}</span>
      <span v-if="secondary" text-xs op70>({{ secondary }})</span>
    </div>
    <div flex flex-1 items-center gap2>
      <div
        :style="{ width: `${widthPercent}%` }"
        h="2.25"
        rounded
        :class="colorClass || 'bg-gradient-from-green-700 bg-gradient-to-green-300 bg-gradient-to-rt'"
        bg-gradient-to-rt
        op90
      />
      <span text-xs op80>{{ progress }}%</span>
      <!-- <span v-if="interval" text-xs op80>{{ interval[0] }}-{{ interval[1] }}%</span> -->
    </div>
  </div>
</template>
