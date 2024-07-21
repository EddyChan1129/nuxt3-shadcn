<script setup>
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";

let data = ref([]);
const list = [
  { title: "Today", component: resolveComponent("TabsToday") },
  { title: "This week", component: resolveComponent("TabsWeek") },
  { title: "This month", component: resolveComponent("TabsMonth") },
  { title: "This year", component: resolveComponent("TabsYear") },
];

let categories = ref({
  today: [
    "00:00",
    "01:00",
    "02:00",
    "03:00",
    "04:00",
    "05:00",
    "06:00",
    "07:00",
    "08:00",
    "09:00",
    "10:00",
    "11:00",
    "12:00",
    "13:00",
    "14:00",
    "15:00",
    "16:00",
    "17:00",
    "18:00",
    "19:00",
    "20:00",
    "21:00",
    "22:00",
    "23:00",
    "24:00",
  ],
  week: [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
  ],
  month: [
    "1",
    "2",
    "3",
    "4",
    "5",
    "6",
    "7",
    "8",
    "9",
    "10",
    "11",
    "12",
    "13",
    "14",
    "15",
    "16",
    "17",
    "18",
    "19",
    "20",
    "21",
    "22",
    "23",
    "24",
    "25",
    "26",
    "27",
    "28",
    "29",
    "30",
    "31",
  ],
  year: [
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
});

let currentCategory = ref(["today"]);

const options = computed(() => ({
  chart: {
    type: "line",
    animation: {
      enable: false,
    },
  },
  legend: {
    enabled: false,
  },
  title: {
    text: "",
  },

  xAxis: {
    gridLineColor: "transparent",
    categories: categories.value[currentCategory.value],
  },
  yAxis: {
    gridLineColor: "transparent",

    title: {
      text: "",
    },
  },
  plotOptions: {
    line: {
      marker: {
        enabled: false,
      },
      dataLabels: {
        enabled: false,
      },
      enableMouseTracking: true,
    },
  },
  series: [
    {
      name: "line",
      lineWidth: "4px",
      color: {
        linearGradient: {},
        stops: [
          [0, "rgba(252,176,69,1)"],
          [0.33, "rgba(253,29,29,1)"],
          [0.66, "rgba(131,58,180,1)"],
          [1, "rgba(29,217,83,1)"],
        ],
      },
      data: data.value,
    },
  ],
}));

const setCategory = (e) => {
  let v = e.target.innerText.toLowerCase();
  currentCategory.value = v;
  switch (v) {
    case "today":
      generateData(24);
      break;
    case "this week":
      generateData(7);
      break;
    case "this month":
      generateData(31);
      break;
    case "this year":
      generateData(12);
      break;
  }
};
function generateData(number = 7) {
  let values = [];
  for (let i = 0; i < number + 1; i++) {
    values.push(Math.floor(Math.random() * 100));
  }
  data.value = values;
  return values;
}

onMounted(() => {
  generateData();
});
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
        <Tabs default-value="today" @click="setCategory">
          <TabsList class="max-w-[400px]">
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
