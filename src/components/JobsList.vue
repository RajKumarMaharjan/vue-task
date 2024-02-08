<template>
  <div>
    <p class="uppercase text-center mt-8 font-semibold underline">Ordered by {{ order }}</p>
    <ul className="w-[80%] mx-auto" >
      <li v-for="job in orderJobs" :key="job.id" class="bg-gray-100 mb-4 p-8 rounded-lg">
        <h2 className="text-xl text-gray-600 font-semibold pb-2 capitalize" >{{ job.title }} in {{ job.location }}</h2>
          <p class="text-[#2e8e65] text-sm font-semibold pb-2">{{ job.salary }} NRP</p>
        <div>
          <p class="text-sm font-thin">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati
            laboriosam ratione reprehenderit nesciunt deserunt possimus nobis
            quod accusamus fugiat magni. Harum commodi ratione porro quia
            tempore cumque, velit accusamus. Repudiandae.
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },

  setup(props) {
    const orderJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return { orderJobs }
  }
});
</script>
