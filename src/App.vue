<template>
<h1 class="uppercase text-center text-[2rem] font-bold mt-10 underline text-[#2e8e65] "><span class="text-5xl">H</span>yrule <span class="text-5xl">J</span>obs</h1>
  <div class="flex flex-wrap gap-4 justify-center mt-6">
    <button
      @click="handleClick('title')"
      className="border border-gray-400 px-3 bg-[#d2e6e1] rounded-md"
    >
      Order By Title
    </button>
    <button
      @click="handleClick('salary')"
      className="border border-gray-400 px-3 bg-[#d2e6e1] rounded-md"
    >
      Order By Salary
    </button>
    <button
      @click="handleClick('location')"
      className="border border-gray-400 px-3 bg-[#d2e6e1] rounded-md"
    >
      Order By Location
    </button>
  </div>
   <div class="text-3xl">
    <JobList :jobs="jobs" :order="order" />
   </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
import JobData from './data/jobData.json'

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>(JobData);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>
