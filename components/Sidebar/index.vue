<template>
  <div class="relative">
    <div class="flex lg:hidden">
      <SidebarMenu />
    </div>
    <div class="lg:flex hidden">
      <SidebarMenu />
    </div>
  </div>
</template>

<script setup>
const open = ref(true);
</script>
