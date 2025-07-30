<template>
  <div class="flex flex-col gap-2">
    <div class="flex flex-col lg:flex-row">
      <div class="w-full lg:w-2/12 font-semibold">Frontend</div>
      <div class="flex flex-col">
        <div>Next.js (app router)</div>
        <div>Typescript</div>
      </div>
    </div>

    <div class="flex flex-col lg:flex-row">
      <div class="w-full lg:w-2/12 font-semibold">Backend</div>
      <div class="flex flex-col">
        <div>Go 1.23</div>
        <div>Gin 1.10</div>
      </div>
    </div>

    <div class="flex flex-col lg:flex-row">
      <div class="w-full lg:w-2/12 font-semibold">Database</div>
      <div>MongoDB</div>
    </div>
    <div class="h-8 flex-none"></div>
  </div>

  <a
    class="font-semibold text-sky-200 hover:text-sky-300 transition-all duration-300 cursor-pointer"
    href="https://expense-tracker-fe-five.vercel.app"
    target="_blank"
  >
    Live demo
  </a>
  <div class="h-8 flex-none"></div>
  <div class="flex flex-col lg:flex-row">
    <div class="w-full lg:w-2/12 font-semibold">Source code</div>
    <div class="flex flex-col">
      <a
        class="text-sky-200 hover:text-sky-300 transition-all duration-300 cursor-pointer"
        href="https://github.com/noverina/expense-tracker-be"
        target="_blank"
      >
        Backend
      </a>
      <a
        class="text-sky-200 hover:text-sky-300 transition-all duration-300 cursor-pointer"
        href="https://github.com/noverina/expense-tracker-fe"
        target="_blank"
      >
        Frontend
      </a>
    </div>
  </div>

  <div class="h-5 flex-none"></div>
  <div>
    <p>
      An expense tracker where user can track down their income, log daily expenses, and see their
      monthly spending breakdown.
    </p>
  </div>
</template>
