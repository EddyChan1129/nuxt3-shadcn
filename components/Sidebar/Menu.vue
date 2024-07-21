<template>
  <div>
    <header
      class="flex items-center gap-2 p-4 hover:scale-[101%] transition cursor-pointer"
    >
      <Logo />
      <p class="font-bold text-black">Nuxt-Finance</p>
    </header>
    <div class="px-4 grow">
      <div class="grid gap-4">
        <NuxtLink
          :href="item.path"
          class="flex items-center gap-2 px-2 py-1 transition rounded cursor-pointer hover:bg-gray-100"
          v-for="(item, index) in items"
          :key="index"
        >
          <Icon :name="item.icon" size="20" color="black" />

          <span> {{ item.title }}</span>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>
const items = ref([
  { title: "Overview", path: "/", icon: "ri:dashboard-line" },
  { title: "Transactions", path: "transactions", icon: "ri:bank-line" },
  { title: "Account", path: "account", icon: "ri:bank-card-line" },
  { title: "Contacts", path: "contacts", icon: "ri:contacts-line" },
  { title: "Settings", path: "settings", icon: "ri:settings-3-line" },
]);
</script>
