<template>
  <div>
    <TestRequest />
    <div v-if="error" class="error">{{ error }}</div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { ApiService } from "@/services/ApiService";
import type { User } from "@/models/User";

import TestRequest from "@/components/TestRequest.vue"

const users = ref<User[]>([]);
const error = ref<string | null>(null);

const apiService = new ApiService("https://jsonplaceholder.typicode.com");

const fetchUsers = async () => {
  try {
    const response = await apiService.get<User[]>("/users");
    users.value = response.data;
  } catch (err) {
    error.value = "Failed to fetch users";
    console.error(err);
  }
};

// Fetch users when the component is mounted
onMounted(fetchUsers);
</script>

<style>
.error {
  color: red;
  font-weight: bold;
}
</style>
