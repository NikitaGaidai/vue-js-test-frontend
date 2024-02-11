<script setup>
import { onMounted } from 'vue'

class BadgeType {
  text = 'gray-600'
  pill = 'gray-400'
  bg = 'gray-100'

  constructor(text, pill, bg) {
    this.text = text
    this.pill = pill
    this.bg = bg
  }
}

const colorMap = {
  default: new BadgeType('text-gray-600', 'fill-gray-400', 'bg-gray-100'),
  error: new BadgeType('text-red-700', 'fill-red-500', 'bg-red-100'),
  warning: new BadgeType('text-yellow-800', 'fill-yellow-500', 'bg-yellow-100'),
  success: new BadgeType('text-green-700', 'fill-green-500', 'bg-green-100'),
}

const props = defineProps({
  type: String,
})

const badgeFill = (type) => {
  switch (type) {
    case 'default':
      return colorMap.default
    case 'error':
      return colorMap.error
    case 'warning':
      return colorMap.warning
    case 'success':
      return colorMap.success
    default:
      return colorMap.default
  }
}

</script>

<template>
  <span :class="'inline-flex items-center gap-x-1.5 rounded-full  px-2 py-1 text-xs font-medium ' + badgeFill(props.type).bg + ' ' + badgeFill(props.type).text">
    <svg :class="'h-2 w-2 ' + badgeFill(props.type).pill" viewBox="0 0 6 6" aria-hidden="true">
      <circle cx="3" cy="3" r="3" />
    </svg>
    <slot>Undefined</slot>
  </span>
</template>

<style scoped>

</style>