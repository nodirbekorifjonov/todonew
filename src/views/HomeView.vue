<script setup lang="ts">
import FormCreate from "@/components/FormCreate.vue";
import TasksList from "@/components/TasksList.vue";
import { onMounted } from "vue";

onMounted(() => {
  if (!localStorage.getItem("tasks")) {
    localStorage.setItem("tasks", JSON.stringify([]));
  }
});
</script>

<template>
  <main class="pt-[91px]">
    <FormCreate class="absolute top-[172px]" />
    <TasksList />
  </main>
</template>
