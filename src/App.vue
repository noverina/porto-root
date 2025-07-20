<template>
  <main class="bg-gray-900 text-white h-screen w-screen text-sm">
    <div class="flex flex-col lg:flex-row p-10 h-full">
      <NavBar
        @change-active-tab="changeActiveTab"
        :current="active"
        class="h-1/12 lg:h-full bg-gray-700 rounded-tl-md rounded-tr-md lg:rounded-tl-lg lg:rounded-bl-lg lg:rounded-tl-lg lg:rounded-tr-none lg:rounded-br-none p-5 w-full lg:w-2/12 lg:overflow-y-scroll"
      ></NavBar>
      <div
        class="w-full h-full bg-gray-800 rounded-bl-md rounded-br-md lg:rounded-tr-lg lg:rounded-br-lg lg:rounded-tl-none lg:rounded-bl-none p-5 overflow-y-scroll"
      >
        <Transition name="fade" mode="out-in">
          <div v-if="active === 1" class="flex flex-col justify-end items-end h-full p-5">
            <HomeView></HomeView>
          </div>
          <div v-else-if="active === 2" class="flex flex-col h-full p-5">
            <ExamView @change-active-tab="changeActiveTab"></ExamView>
          </div>
          <div v-else-if="active === 3" class="p-5">
            <ExamCaseStudy @change-active-tab="changeActiveTab"></ExamCaseStudy>
          </div>
          <div v-else-if="active === 4" class="flex flex-col h-full p-5">
            <ExpenseView></ExpenseView>
          </div>
        </Transition>

        <div v-show="active === 3"></div>
      </div>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import NavBar from './components/NavBar.vue'
import HomeView from '@/components/HomeView.vue'
import ExamView from './components/ExamView.vue'
import ExamCaseStudy from './components/ExamCaseStudy.vue'
import ExpenseView from './components/ExpenseView.vue'

const active = ref(1)

const changeActiveTab = (key: number) => {
  active.value = key
}
</script>
