<template>
  <div class="grid gap-4 w-full">
    <header class="flex justify-between">
      <div class="grow">
        <p>Hi, Welcome Eddy Dashboard !</p>
        <h1>Dash board</h1>
      </div>

      <div class="w-[120px] h-[36px] bg-neutral-200"></div>
    </header>
    <main class="grid gap-2">
      <div class="flex items-center gap-4">
        <div
          v-for="(item, index) in 3"
          :key="index"
          class="w-[120px] h-[36px] bg-neutral-200"
        ></div>
      </div>
      <section>
        <div class="w-full h-[360px] bg-neutral-200"></div>
      </section>
    </main>
    <footer class="flex items-center gap-4">
      <div
        v-for="(item, index) in 3"
        :key="index"
        class="w-full h-[260px] bg-neutral-200"
      ></div>
    </footer>
  </div>
</template>
<script setup>
const loading = ref(false);
</script>
