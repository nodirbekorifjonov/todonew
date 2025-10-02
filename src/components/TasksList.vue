<script setup lang="ts">
import Task from "./Task.vue";
import TasksHeader from "./TasksHeader.vue";

const tasks = [
  { id: 1, text: "Sample Task 1" },
  { id: 2, text: "Sample Task 2" },
];
</script>

<template>
  <section>
    <div class="site-container">
      <TasksHeader />
      <div class="flex flex-col gap-3 pt-6">
        <Task v-for="task in tasks" :key="task.id" :task="task" />
      </div>
    </div>
  </section>
</template>

<style scoped></style>
