<script lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup

import { ref } from "vue";
import { fakeJobs } from "./fakeData/data";
import Job from "./types/Job";
import JobList from "./components/JobList.vue";
import OrderTerm from "./types/orderTerm";
export default {
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>(fakeJobs);
    const order = ref<OrderTerm>("title");

    const handleClicks = (term: OrderTerm) => {
      order.value = term;
    };

    return {
      jobs,
      handleClicks,
      order,
    };
  },
};
</script>

<template>
  <div class="app">
    <header>
      <button @click="handleClicks('title')">Order by Title</button>
      <button @click="handleClicks('salary')">Order by Salary</button>
      <button @click="handleClicks('location')">Order by Location</button>
    </header>
    <!-- using component and passing props -->
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
