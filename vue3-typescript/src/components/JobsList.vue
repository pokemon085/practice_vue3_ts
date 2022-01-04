<template>
  <div>
    <div class="job-list">
      <p>Ordered by {{ order }}</p>
      <ul>
        <li v-for="job in orderedJobs" :key="`key-${job.id}`">
          <h2>{{ job.title }} in {{ job.location }}</h2>
          <div class="salary">
            <p>{{ job.salary }}</p>
          </div>
          <div class="description">
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit.
              Provident illo, cupiditate temporibus nisi nam sunt, obcaecati
              tempore excepturi sint totam est ratione eum. Illo in dolorum sed
              consequuntur quos perferendis?
            </p>
          </div>
        </li>
      </ul>
    </div>
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
      //注意 透過props把jobs資料傳過來 還需要引入Job所定義的資料型態 才不會報錯
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });
    return {orderedJobs}
  },
});
</script>

