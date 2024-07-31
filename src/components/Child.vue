<script setup lang="ts">
export interface IUser {
  body: string;
  id: number;
  title: string;
  userId: number;
}
export interface Props {
  title: string;
  isLoading: boolean;
  data: IUser | null;
}
defineProps<Props>();
</script>

<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col>
          <div v-if="isLoading">
            <v-progress-circular indeterminate></v-progress-circular>
          </div>
          <div v-else>
            <pre>{{ data }}</pre>
            <h3>Data loaded properly</h3>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>
