<template>
  <div class="flex flex-col gap-2">
    <div class="flex flex-col lg:flex-row">
      <div class="w-full lg:w-2/12 font-semibold">Frontend</div>
      <div class="flex flex-col">
        <div>Vue 3</div>
        <div>Typescript</div>
        <div>Pinia</div>
      </div>
    </div>
    <div class="flex flex-col lg:flex-row">
      <div class="w-full lg:w-2/12 font-semibold">Backend</div>
      <div class="flex flex-col">
        <div>Java 21</div>
        <div>Spring Boot 3 with JPA</div>
      </div>
    </div>
    <div class="flex flex-col lg:flex-row">
      <div class="w-full lg:w-2/12 font-semibold">Database</div>
      <div>SQLite</div>
    </div>
    <div class="h-8 flex-none"></div>
  </div>

  <a
    class="font-semibold text-sky-200 hover:text-sky-300 transition-all duration-300 cursor-pointer"
    href="exam-fe-tau.vercel.app"
    target="_blank"
  >
    Live demo
  </a>
  <div
    class="font-semibold text-sky-200 hover:text-sky-300 transition-all duration-300 cursor-point cursor-pointer"
    @click="emit('change-active-tab', 3)"
  >
    Case study: Avoiding O(N+1) problem using flat query
  </div>
  <div class="h-8 flex-none"></div>
  <div class="flex flex-col lg:flex-row">
    <div class="w-full lg:w-2/12 font-semibold">Source code</div>
    <div class="flex flex-col">
      <a
        class="text-sky-200 hover:text-sky-300 transition-all duration-300 cursor-pointer"
        href="https://github.com/noverina/exam-be"
        target="_blank"
      >
        Backend
      </a>
      <a
        class="text-sky-200 hover:text-sky-300 transition-all duration-300 cursor-pointer"
        href="https://github.com/noverina/exam-fe"
        target="_blank"
      >
        Frontend
      </a>
    </div>
  </div>

  <div class="h-8 flex-none"></div>
  <div>
    <p>
      A multi-role multiple-choice-question exam application. Teacher can create & update exam,
      grade exam, and see how students perform in a given exam. Student can 'take' exam by selecting
      answers & submitting them and then see how they perform in said exam.
    </p>
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits<{ (e: 'change-active-tab', key: number): void }>()
</script>
