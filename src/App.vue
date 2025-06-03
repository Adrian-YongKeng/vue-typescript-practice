<template>
  <div class="app">
    <!-- <p>{{ name }} - {{ age }}</p>

    <button @click="changeName('Zebra')">Change name</button>
    <button @click="changeAge(30)">Change age</button> -->

    <!-- <p>{{ jobs[0].location }}</p> -->

    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import JobList from "./components/JobList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    // const state = reactive({
    //   name: "Link",
    //   age: 25 as number | string,
    // });

    // return { ...toRefs(state) };

    // const name = ref("Link");
    // const age = ref<number | string>(25);

    // return { age, name };

    const jobs = ref<Job[]>([
      {
        title: "farm worker",
        location: "Kuala Selangor",
        salary: 300000,
        id: "1",
      },
      {
        title: "quarry man",
        location: "Hulu Selangor",
        salary: 400000,
        id: "2",
      },
      { title: "player", location: "Hilir Selangor", salary: 350000, id: "3" },
      { title: "fisherman", location: "Port Klang", salary: 630000, id: "4" },
      { title: "Body Guard", location: "Kuala Lumpur", salary: 50000, id: "5" },
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
  // data() {
  //   return {
  //     name: "Link",
  //     age: 25 as number | string,
  //   };
  // },
  // methods: {
  //   changeName(name: string) {
  //     this.name = name;
  //     return name;
  //   },
  //   changeAge(age: number | string) {
  //     this.age = age;
  //     return age;
  //   },
  // },
});
</script>

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
