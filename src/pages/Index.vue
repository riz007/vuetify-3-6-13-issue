<script setup lang="ts">
import { useRouter } from "vue-router";

const router = useRouter();
const toPage = () => {
  router.push("/page");
};
</script>

<template>
  <v-btn @click="toPage" color="primary">Click</v-btn>
</template>
