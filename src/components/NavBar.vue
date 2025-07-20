<template>
  <header>
    <nav
      class="flex flex-row flex-wrap lg:flex-col justify-center lg:justify-start items-start gap-4"
    >
      <NavButton :index="1" :current="current" @change-active-tab="onClick">Home</NavButton>
      <div class="hidden lg:block">Sample projects</div>
      <NavButton :index="2" :current="current" @change-active-tab="onClick">Exam</NavButton>
      <NavButton :index="4" :current="current" @change-active-tab="onClick">Expense</NavButton>
    </nav>
  </header>
</template>

<script setup lang="ts">
interface Props {
  current: number
}
defineProps<Props>()

import NavButton from './NavButton.vue'
const emit = defineEmits<{ (e: 'change-active-tab', key: number): void }>()
const onClick = (key: number) => {
  emit('change-active-tab', key)
}
</script>
