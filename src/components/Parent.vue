<script setup lang="ts">
import { defineAsyncComponent, ref, onMounted } from "vue";
import axios from "axios";
import { IUser } from "./Child.vue";

const Child = defineAsyncComponent(() => import("./Child.vue"));
const isLoading = ref(false);
const data = ref<IUser | null>(null);

const doSomething = () =>
  new Promise((resolve, reject) => {
    axios
      .get("https://jsonplaceholder.typicode.com/posts/1")
      .then((response) => {
        data.value = response.data;
        resolve(response.data);
      })
      .catch(() => {
        reject();
      });
  });

onMounted(async () => {
  isLoading.value = true;
  await doSomething();
  isLoading.value = false;
});
</script>

<template>
  <Child title="Child" :is-loading="isLoading" :data="data" />
</template>
