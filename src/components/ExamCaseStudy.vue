<template>
  <div>
    <button
      @click="emit('change-active-tab', 2)"
      class="absolute right-15 top-30 lg:right-15 lg:top-15 z-10 bg-gray-700 opacity-60 text-sky-300 transform hover:opacity-100 hover:bg-slate-700 rounded-md w-8 h-8 flex justify-center items-center cursor-pointer transition-all duration-300"
    >
      ←
    </button>
    <div class="flex flex-col gap-8">
      <div class="flex flex-col gap-2">
        <h1 class="font-semibold text-lg">Problem and Context</h1>
        <p>
          In realistic enterprise systems, querying parent entities along with children would
          triggers the notorious O(N+1) query problem. For example, fetching an exam alongside its
          related questions and answers naively cause multiple database round-trips, drastically
          slowing down performance. Common Hibernate strategies like JOIN FETCH, @EntityGraph, or
          batched fetches may still produce hidden inefficiencies or rigid field selection.
        </p>
      </div>
      <div class="flex flex-col gap-2">
        <h1 class="font-semibold text-lg">
          Solution: Single Flat Query Paired with Manual DTO Reshaping
        </h1>
        <p>
          Rather than relying on ORM fetch tactics, I implemented a single flat SQL query via JPA to
          fetch exactly the required columns across parent-child relationships. Then, I used
          projection/ constructor expression to map the columns into DTO with minimal memory usage.
          Further, I manually restructured the flat results into nested Java DTOs (exam → questions
          → answers). This precise approach prevent O(N+1) query problem, avoids full entity
          hydration, and grants total control over the query.
        </p>
      </div>
      <div class="flex flex-col gap-2">
        <h1 class="font-semibold text-lg">Impact and Result</h1>
        <ul class="list-none pl-5 flex flex-col gap-2">
          <li>
            <span class="font-semibold">Reduced round-trips:</span>
            from O(N+1) to a single query per request, leading to significant cut on DB I/O load and
            overall performance boost.
          </li>
          <li>
            <span class="font-semibold">Memory optimization:</span>
            using constructor expression lead to precise columns selection, avoiding unnecessary
            memory usage.
          </li>
        </ul>
      </div>
      <div class="flex flex-col gap-2">
        <h1 class="font-semibold text-lg">Trade-Off and Learning</h1>
        <ul class="list-none pl-5 flex flex-col gap-2">
          <li>
            <span class="font-semibold">More complex service layer:</span>
            manual reshaping requires nested loops, which leads to more verbose code. This can be
            somewhat mitigated by Streams, which lead to the second point;
          </li>
          <li>
            <span class="font-semibold">Maintainability:</span>
            using Streams looked elegant but it was difficult to debug. Furthermore, flat query
            result in Cartesian product that can be confusing to read.
          </li>
          <li>
            <span class="font-semibold">CPU overhead:</span>
            flattened data means heavier reshaping in memory which is an acceptable trade-off since
            CPU beats DB I/O latency.
          </li>
          <li>
            <span class="font-semibold">Performance nuance:</span>
            in a 50 query benchmark, flat query outperformed JOIN FETCH and @EntityGraph, however
            only by a minimal nanoseconds amount.
          </li>
        </ul>
      </div>
      <div class="flex flex-col gap-2">
        <h1 class="font-semibold text-lg">Future Improvement</h1>
        <ul class="list-none pl-5 flex flex-col gap-2">
          <li>
            <span class="font-semibold">Hybrid batch fetching (@BatchSize):</span>
            for selective dataset loads to scale with large datasets.
          </li>
          <li>
            <span class="font-semibold">Indexing & caching optimizations:</span>
            on high-traffic columns (e.g. course_id, user_id).
          </li>
          <li>
            <span class="font-semibold">Query instrumentation tools:</span>
            use tools like Hibernate stats or SQL explain to further detect potential O(N+1)
            problem.
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits<{ (e: 'change-active-tab', key: number): void }>()
</script>

<style scoped>
ul li::marker {
  content: '- ';
}
</style>
