<script setup>
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";

const list = [
  { title: "Today", component: resolveComponent("TabsToday") },
  { title: "This week", component: resolveComponent("TabsWeek") },
  { title: "This month", component: resolveComponent("TabsMonth") },
  { title: "This year", component: resolveComponent("TabsYear") },
];

const options = computed(() => ({
  chart: {
    type: "line",
    animation: {
      enable: false,
    },
  },
  title: {
    text: "",
  },

  xAxis: {
    categories: [
      "Jan",
      "Feb",
      "Mar",
      "Apr",
      "May",
      "Jun",
      "Jul",
      "Aug",
      "Sep",
      "Oct",
      "Nov",
      "Dec",
    ],
  },
  yAxis: {
    title: {
      text: "Temperature (°C)",
    },
  },
  plotOptions: {
    line: {
      dataLabels: {
        enabled: true,
      },
      enableMouseTracking: false,
    },
  },
  series: [
    {
      name: "Reggane",
      data: [
        16.0, 18.2, 23.1, 27.9, 32.2, 36.4, 39.8, 38.4, 35.5, 29.2, 22.0, 17.8,
      ],
    },
    {
      name: "Tallinn",
      data: [
        -2.9, -3.6, -0.6, 4.8, 10.2, 14.5, 17.6, 16.5, 12.0, 6.5, 2.0, -0.9,
      ],
    },
  ],
}));
</script>

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
      <template>
        <Tabs default-value="today" class="w-[400px]">
          <TabsList>
            <TabsTrigger
              v-for="(item, index) in list"
              :key="index"
              :value="item.title"
            >
              {{ item.title }}
            </TabsTrigger>
          </TabsList>
          <TabsContent
            v-for="(item, index) in list"
            :key="index"
            :value="item.title"
          >
            <component :is="item.component" />
            <highchart :options="options" />
          </TabsContent>
        </Tabs>
      </template>
      <!-- <div class="flex items-center gap-4">
        <div
          v-for="(item, index) in 3"
          :key="index"
          class="w-[120px] h-[36px] bg-neutral-200"
        ></div>
      </div>
      <section>
        <div class="w-full h-[360px] bg-neutral-200"></div>
      </section> -->
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
