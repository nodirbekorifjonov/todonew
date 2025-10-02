<script setup lang="ts">
import FormCreate from "@/components/FormCreate.vue";
import TasksList from "@/components/TasksList.vue";

localStorage.setItem("tasks", "[]");
</script>

<template>
  <main class="pt-[91px]">
    <FormCreate class="absolute top-[172px]" />
    <TasksList />
  </main>
</template>
