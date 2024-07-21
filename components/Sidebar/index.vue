<template>
  <div>
    <div
      class="z-50 flex items-center justify-between w-full h-full p-4 lg:hidden"
    >
      <Logo />
      <Icon
        name="iconamoon:menu-burger-horizontal"
        class="z-50 cursor-pointer left-2 top-2"
        size="30"
        @click="open = !open"
      />

      <div v-if="open" class="fixed top-0 left-0 z-50 w-full h-full bg-white">
        <Icon
          name="material-symbols:close"
          class="absolute z-50 cursor-pointer right-4 top-2"
          size="30"
          @click="open = !open"
        />
        <SidebarMenu />
      </div>
    </div>

    <div
      class="lg:flex hidden w-[250px] h-screen flex-col justify-between border-r"
    >
      <SidebarMenu />
      <div>UserItem</div>
    </div>
  </div>
</template>

<script setup>
const open = ref(true);
</script>
