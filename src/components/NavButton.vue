<template>
  <button
    @click="emit('change-active-tab', index)"
    class="px-4 cursor-pointer text-sky-200 hover:text-sky-300 transition-all duration-300 font-semibold text-left"
    :class="{
      'border-l-2 border-gray-400 ml-2 text-sky-300! hover:text-cyan-400!': isCurrent,
    }"
  >
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
import { computed } from 'vue'
interface Props {
  index: number
  current: number
}

const props = defineProps<Props>()

const emit = defineEmits<{ (e: 'change-active-tab', key: number): void }>()
const isCurrent = computed(() =>
  props.current === 3 || props.current === 5
    ? props.current === props.index || props.current - 1 === props.index
    : props.current === props.index,
)
</script>
