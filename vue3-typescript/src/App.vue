<template>
  <div class="app">
    <div class="job" v-for="item in job" :key="item.id">
      title: {{ item.title }}, location: {{ item.location }}, salary:
      {{ item.salary }}, id: {{ item.id }}<br />
    </div>
    <hr />
    <div class="order">
      <button @click="handleClick('title')">order by title</button>
      <button @click="handleClick('salary')">order by salary</button>
      <button @click="handleClick('location')">order by location</button>
    </div>
    <job-list :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/JobsList.vue";
export default defineComponent({
  name: "App",
  components: {
    JobList,
  },
  setup() {
    const jobs = ref<Job[]>([
      { title: "farm worker", location: "New York", salary: 30000, id: "11" },
      { title: "quarryman", location: "London", salary: 40000, id: "22" },
      { title: "flute player", location: "Lagos", salary: 35000, id: "33" },
      { title: "fisherman", location: "Boston", salary: 21000, id: "44" },
      {
        title: "prison guard",
        location: "San Francisco",
        salary: 32000,
        id: "55",
      },
    ]);
    const order = ref<OrderTerm>("title"); //預設以title排序
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return {
      jobs,
      order,
      handleClick,
    };
  },
  data() {
    return {
      job: [
        {
          title: "React developer",
          location: "New York",
          salary: 30000,
          id: "1",
        },
        {
          title: "Nodejs developer",
          location: "London",
          salary: 40000,
          id: "2",
        },
        {
          title: "Flutter developer",
          location: "Lagos",
          salary: 35000,
          id: "3",
        },
        {
          title: "Vuejs developer",
          location: "Boston",
          salary: 21000,
          id: "4",
        },
        {
          title: "Svelte developer",
          location: "San Francisco",
          salary: 32000,
          id: "5",
        },
      ] as Job[],
    };
  },
});
</script>

<style>

.order{
  text-align: center;
  margin-top:20px;
}
button{
  margin:0 10px;
  color:#1195c9;
  border:3px solid #1195c9;
  background: #d5f0ff;
  padding:8px 16px;
  border-radius: 4px;
  cursor:pointer;
  font-weight: bold;

}
</style>
